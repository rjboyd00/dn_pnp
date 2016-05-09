denovo notes



Last login: Tue Mar  8 23:34:02 on ttys002
~ Ryan$ cd Documents/
Documents Ryan$ git init dn_pnp
Initialized empty Git repository in /Users/Ryan/Documents/dn_pnp/.git/
Documents Ryan$ cd dn_pnp/
dn_pnp Ryan$ mkdir theozyme prep runs
dn_pnp Ryan$ ls
README.md	prep		runs		theozyme
dn_pnp Ryan$ cd theozyme/
theozyme Ryan$ ls
theozyme Ryan$ pymol
 PyMOL(TM) 1.7.4.5 Edu - Educational Product
 Copyright (C) Schrodinger, LLC

... 

PyMOL>pwd
/Users/Ryan/Documents/dn_pnp/theozyme
PyMOL>fetch 3phb
 please wait ...
HEADER    TRANSFERASE/TRANSFERASE INHIBITOR       03-NOV-10   3PHB
TITLE     CRYSTAL STRUCTURE OF HUMAN PURINE NUCLEOSIDE PHOSPHORYLASE IN COMPLEX
TITLE    2 WITH DADME-IMMG
COMPND    MOL_ID: 1;
COMPND   2 MOLECULE: PURINE NUCLEOSIDE PHOSPHORYLASE;
COMPND   3 CHAIN: E, Q, S, T, U, Y;
COMPND   4 SYNONYM: PNP, INOSINE PHOSPHORYLASE;
COMPND   5 EC: 2.4.2.1;
COMPND   6 ENGINEERED: YES
 ObjectMolecule: Read secondary structure assignments.
 ObjectMolecule: Read crystal symmetry information.
 Symmetry: Found 4 symmetry operators.
 CmdLoad: "./3phb.pdb" loaded as "3phb".
 parser: no matching files.
PyMOL>create chaina, chain a  <--had to re-do on chain e
 Selector: found 0 atoms.
 Executive: object "chaina" created.
PyMOL>create chaina, chain e
 Selector: found 2298 atoms.
PyMOL>save crystal_chainA.pdb
 Save: wrote "crystal_chainA.pdb".
theozyme Ryan$ ls
3phb.pdb		crystal_chainA.pdb
theozyme Ryan$ git add 3phb.pdb crystal_chainA.pdb 

theozyme Ryan$ git commit -m 'added crystal structure and chain A'
[master (root-commit) 38dc10f] added crystal structure and chain A
 Committer: Ryan Boyd <Ryan@resnet-103-042.ucdavis.edu>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly:

    git config --global user.name "Your Name"
    git config --global user.email you@example.com

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 2 files changed, 17569 insertions(+)
 create mode 100644 theozyme/3phb.pdb
 create mode 100644 theozyme/crystal_chainA.pdb

theozyme Ryan$ open crystal_chainA.pdb 
theozyme Ryan$ pwd
/Users/Ryan/Documents/dn_pnp/theozyme
theozyme Ryan$ cp ~/Downloads/LG_0001.pdb .
theozyme Ryan$ 

# used avogadro to attach phosphate to ligand (rosetta matcher cant use 2 ligands) <--

 <--used molfile_to_params.py script to generate params file

theozyme Ryan$ python2 /Applications/rosetta_bin_mac_2016.10.58534_bundle/main/source/scripts/python/public/molfile_to_params.py -n LG1 LG1.mol2

Centering ligands at ( -44.231,    0.280,   -3.255)
Atom names contain duplications -- renaming all atoms.
WARNING:  atom  C9  has valence > 4
WARNING:  atom  P1  has valence > 4
Partial charges already fully assigned, no changes made; net charge -1.000
WARNING: fragment 1 has 26 total atoms including H; protein residues have 7 - 24 (DNA: 33)
WARNING: fragment 1 has 25 non-H atoms; protein residues have 4 - 14 (DNA: 22)
Average 26.0 atoms (25.0 non-H atoms) per fragment
(Proteins average 15.5 atoms (7.8 non-H atoms) per residue)
WARNING:  no root atom specified, using NBR atom instead.
Wrote PDB file LG1_0001.pdb
Wrote params file LG1.params
theozyme Ryan$  


alex@lab$ ls
LG.params       LG_0001.pdb     obj02.pdb       tss.mol2

alex@lab$ mv LG.params LG1.params

alex@lab$ ls
LG1.params      LG_0001.pdb     obj02.pdb       tss.mol2




 <-- redo and make to strongest H-bond. check bond valence in avogadro...make lig and phos an object in pymol and open in avogadro --> save as tss.mol2 --> run python molfile_to_params.py tss.mol2 --> see email
