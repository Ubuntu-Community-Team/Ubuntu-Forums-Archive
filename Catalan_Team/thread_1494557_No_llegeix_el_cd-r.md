---
title: "No llegeix el cd-r"
date: 2010-05-27
forum: Catalan Team
---

### Post by roquet on 2010-05-27
Bé el lector ha deixat de llegir-me els cd-r que tinc gravats, ja que n'he provat 10 cd-r gravats en diferents equips, marques, i amb més o menys temps i tots me'ls detecta com a cd verges. només detecta com a reals els cds originals. 

creieu que podria tractar-se d'error de hardware? 

moltes gràcies.

Editat

sembla ser que es tracta d'un bug que diria que he trobat la solució [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/562092]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/562092") s'ha de canviar kernel al 2.6.34. més tard torno a editar per si s'ha arreglat.

edició 2
tampoc m'ha funcionat ni amb el kernel 2.6.34 ni amb el kernel 2.6.30.

Edició 3

ja funciona, amb l'últimca actualització del kernel ja em va.

---

### Post by wgarcia on 2010-05-27
Posa un CD, i de seguida des d'una terminal entra la comanda "dmesg" i mira al final de les línies que surt a veure si et sembla que hi hagi algun error relacionat amb el lector de CD.

---

### Post by roquet on 2010-05-27
company wgarcia, em surt això referit al cd

> 182.213219] cdrom: This disc doesn't have any tracks I recognize!
[  182.248148] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.248163] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.248177] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.248190] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.248215] end_request: I/O error, dev sr0, sector 0
[  182.248226] __ratelimit: 18 callbacks suppressed
[  182.248235] Buffer I/O error on device sr0, logical block 0
[  182.251780] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.251789] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.251798] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.251809] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.251831] end_request: I/O error, dev sr0, sector 0
[  182.251838] Buffer I/O error on device sr0, logical block 0
[  182.255417] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.255428] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.255437] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.255448] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.255469] end_request: I/O error, dev sr0, sector 0
[  182.255477] Buffer I/O error on device sr0, logical block 0
[  182.259806] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.259822] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.259835] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.259848] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.259869] end_request: I/O error, dev sr0, sector 0
[  182.259881] Buffer I/O error on device sr0, logical block 0
[  182.263301] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.263317] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.263329] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.263343] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.263365] end_request: I/O error, dev sr0, sector 0
[  182.263378] Buffer I/O error on device sr0, logical block 0
[  182.265905] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.265922] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.265935] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.265948] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.265970] end_request: I/O error, dev sr0, sector 0
[  182.265982] Buffer I/O error on device sr0, logical block 0
[  182.268264] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.268273] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.268283] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.268293] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.268314] end_request: I/O error, dev sr0, sector 0
[  182.268322] Buffer I/O error on device sr0, logical block 0
[  182.270561] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.270569] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.270579] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.270590] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.270611] end_request: I/O error, dev sr0, sector 0
[  182.270618] Buffer I/O error on device sr0, logical block 0
[  182.272858] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.272868] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.272880] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.272893] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.272915] end_request: I/O error, dev sr0, sector 0
[  182.272923] Buffer I/O error on device sr0, logical block 0
[  182.275258] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.275268] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.275279] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.275292] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.275314] end_request: I/O error, dev sr0, sector 0
[  182.275323] Buffer I/O error on device sr0, logical block 0
[  182.277583] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.277594] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.277603] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.277614] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.277635] end_request: I/O error, dev sr0, sector 0
[  182.279917] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.279925] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.279935] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.279947] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.279968] end_request: I/O error, dev sr0, sector 0
[  182.282209] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.282218] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.282227] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.282238] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.282259] end_request: I/O error, dev sr0, sector 0
[  182.284515] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.284525] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.284536] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.284549] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.284571] end_request: I/O error, dev sr0, sector 0
[  182.286896] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.286906] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.286918] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.286930] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.286952] end_request: I/O error, dev sr0, sector 0
[  182.289186] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.289197] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.289208] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.289221] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.289243] end_request: I/O error, dev sr0, sector 0
[  182.291504] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.291514] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.291525] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.291538] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.291561] end_request: I/O error, dev sr0, sector 0
[  182.293796] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.293806] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.293817] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.293829] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.293852] end_request: I/O error, dev sr0, sector 0
[  182.296140] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.296158] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.296180] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.296201] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.296258] end_request: I/O error, dev sr0, sector 0
[  182.299100] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.299117] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.299129] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.299142] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.299165] end_request: I/O error, dev sr0, sector 0
[  182.302172] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.302187] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.302198] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.302211] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.302232] end_request: I/O error, dev sr0, sector 0
[  182.304598] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.304610] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.304619] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.304631] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.304651] end_request: I/O error, dev sr0, sector 0
[  182.307092] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.307103] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.307113] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.307125] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.307145] end_request: I/O error, dev sr0, sector 0
[  182.309590] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.309600] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.309610] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.309621] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.309641] end_request: I/O error, dev sr0, sector 0
[  182.311907] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.311916] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.311925] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.311936] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.311956] end_request: I/O error, dev sr0, sector 0
[  182.317120] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.317134] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.317145] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.317159] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.317180] end_request: I/O error, dev sr0, sector 0
[  182.321297] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.321314] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.321325] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.321338] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.321359] end_request: I/O error, dev sr0, sector 0
[  182.323810] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.323828] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.323840] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.323855] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.323877] end_request: I/O error, dev sr0, sector 0
[  182.326613] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.326628] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.326639] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.326651] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.326672] end_request: I/O error, dev sr0, sector 0
[  182.329576] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.329597] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.329608] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.329622] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.329645] end_request: I/O error, dev sr0, sector 0
[  182.332298] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.332319] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.332333] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.332349] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.332373] end_request: I/O error, dev sr0, sector 0
[  182.334917] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.334928] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.334938] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.334949] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.334969] end_request: I/O error, dev sr0, sector 0
[  182.337296] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.337307] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.337318] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.337332] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.337353] end_request: I/O error, dev sr0, sector 0
[  182.339593] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.339604] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.339617] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.339629] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.339651] end_request: I/O error, dev sr0, sector 0
[  182.341879] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.341890] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.341901] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.341914] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.341937] end_request: I/O error, dev sr0, sector 0
[  182.344210] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.344226] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.344248] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.344270] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.344327] end_request: I/O error, dev sr0, sector 0
[  182.346610] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.346623] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.346635] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.346648] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.346671] end_request: I/O error, dev sr0, sector 0
[  182.348939] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.348950] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.348962] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.348975] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.348996] end_request: I/O error, dev sr0, sector 0
[  182.351322] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.351333] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.351344] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.351357] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.351379] end_request: I/O error, dev sr0, sector 0
[  182.353734] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.353743] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.353753] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.353765] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.353786] end_request: I/O error, dev sr0, sector 0
[  182.356047] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.356063] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.356074] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.356086] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.356108] end_request: I/O error, dev sr0, sector 0
[  182.358635] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.358651] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.358663] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.358677] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.358699] end_request: I/O error, dev sr0, sector 0
[  182.361014] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.361025] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.361036] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.361049] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.361071] end_request: I/O error, dev sr0, sector 0
[  182.363321] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.363332] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.363344] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.363356] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.363378] end_request: I/O error, dev sr0, sector 0
[  182.365652] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.365663] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.365675] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.365687] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.365710] end_request: I/O error, dev sr0, sector 0
[  182.367961] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.367972] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.367983] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.367997] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.368047] end_request: I/O error, dev sr0, sector 0
[  182.370321] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.370333] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.370344] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.370357] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.370379] end_request: I/O error, dev sr0, sector 0
[  182.372699] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.372708] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.372717] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.372728] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.372748] end_request: I/O error, dev sr0, sector 0
[  182.378239] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.378261] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.378273] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.378288] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.378313] end_request: I/O error, dev sr0, sector 0
[  182.380788] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  182.380804] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  182.380815] sr 0:0:1:0: [sr0] Add. Sense: Logical block address out of range
[  182.380827] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  182.380849] end_request: I/O error, dev sr0, sector 0


---

### Post by wgarcia on 2010-05-27
Quan comences el sistema tens nuclis més vells per provar d'arrencar amb ells? Vull dir, des de la pantalla inicial del grub, pots iniciar amb un nucli més antic? Si tens nuclis més antics prova el CD arrencant amb ells a veure si el CD funciona.

---

### Post by roquet on 2010-05-27
tinc la 2.6.31-21 i la 2.6.31-22, si és cert que durant l'actualitazció (que vaig fer ahir i no vaig provar cap cd) vaig eliminar els kernels més vells.  instal·lo la 2.6.32 a veure si ja em va. gràcies pel consell.

---

### Post by papapep on 2010-05-27
Roquet, quan tingueu tant de text poseu-lo en fitxer adjunt, no ho enganxeu directament al fòrum, si us plau.

---

### Post by wgarcia on 2010-05-29
> **roquet said:**
> tinc la 2.6.31-21 i la 2.6.31-22, si és cert que durant l'actualitazció (que vaig fer ahir i no vaig provar cap cd) vaig eliminar els kernels més vells.  instal·lo la 2.6.32 a veure si ja em va. gràcies pel consell.

Si tens Lucid hauries de tenir els nuclis que comencen amb 2.6.32

---

