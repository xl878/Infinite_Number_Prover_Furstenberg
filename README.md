# Infinite_Number_Prover_Furstenberg
Project Overview: https://sites.google.com/scarletmail.rutgers.edu/640-300-h2-final-project/home

-----------------------------------------------------------------------------------------------------------------------------------------------------
**Reference and Acknowledgment**
-----------------------------------------------------------------------------------------------------------------------------------------------------
This Lean development is adapted from and inspired by the Isabelle/HOL formalization of Furstenberg’s topology in the Archive of Formal Proofs.
The overall conceptual structure and several proof strategies follow Eberl’s Isabelle version, but the Lean codebase is an independent re-implementation with Lean-specific definitions, auxiliary lemmas, and topological constructions.

Reference:
Manuel Eberl. *Furstenberg’s Topological Proof of the Infinitude of Primes.*
Archive of Formal Proofs, 2025.
https://www.isa-afp.org/entries/Furstenberg_Topology.html

PDF Outline: https://www.isa-afp.org/browser_info/current/AFP/Furstenberg_Topology/outline.pdf

-----------------------------------------------------------------------------------------------------------------------------------------------------
**Relation to the Isabelle/HOL Formalization**
-----------------------------------------------------------------------------------------------------------------------------------------------------
This project is not a port of the Isabelle AFP entry.
It follows the same broad mathematical outline but implements the theory directly in Lean 4 and Mathlib.

The Lean development, therefore, differs structurally from the Isabelle version due to:
1. Lean’s typeclass system vs. Isabelle’s locale infrastructure,
2. different topological foundations,
3. different algebraic libraries,
4. explicit constructive reasoning where Isabelle uses automation.

Thus, the project should be viewed as a Lean-native reconstruction of Furstenberg’s argument, informed by the Isabelle presentation but developed independently.

-----------------------------------------------------------------------------------------------------------------------------------------------------
**Academic Practice Disclaimer**
-----------------------------------------------------------------------------------------------------------------------------------------------------
This repository is part of a personal academic exploration of formalizing classical number-theoretic arguments in the Lean theorem prover.
Although care has been taken to maintain mathematical correctness and proper citation, this development:
1. is not an officially reviewed mathlib contribution,
2. contains constructions and axioms that may require refinement before reuse,
3. may diverge from Isabelle’s implementation for conceptual or technical reasons.

Users who cite, depend on, or extend this code should apply appropriate academic caution and verify components as needed.

-----------------------------------------------------------------------------------------------------------------------------------------------------
**Lean-Specific Aspects**
-----------------------------------------------------------------------------------------------------------------------------------------------------
Key components that are unique to the Lean formalization:
1. Separate topology space: FbInt := ULift ℤ, ensuring the Furstenberg topology does not interfere with the usual integer topology.
2. Transport lemmas: liftSet, arithProgF_eq_liftSet, etc., connecting ℤ-based arithmetic progressions with their FbInt versions.
3. Residue-class decomposition: The complement of arithProg a b is expressed explicitly as a finite union of the other residue classes: complement(arithProg a b) =
  ⋃ over all i ∈ {1, 2, ..., b−1} of arithProg (a + i) b
(Written using Fin b subtypes in Lean.)
4. Arithmetic reasoning: Use of Int.ModEq, Int.modEq_iff_dvd, injectivity via mul_left_cancel₀, and explicit constructive proofs instead of Isabelle automation.
5. Topology generation: Use of Lean’s generateFrom plus a custom neighborhood-basis axiom to prove: every nonempty open set in the Furstenberg topology is infinite.

A more detailed comparison will appear in: docs/lean-notes.md (Design notes and Isabelle ↔ Lean commentary).
