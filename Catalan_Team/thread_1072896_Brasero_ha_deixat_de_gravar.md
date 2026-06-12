---
title: "Brasero ha deixat de gravar"
date: 2009-02-17
forum: Catalan Team
---

### Post by jinglada on 2009-02-17
Estava fent proteccions de fitxers i carpetes i tot d'una Brasero ha començat a donar el següent error:

Session error : no es pot bloquejar la unitat (procés d'enregistrament en curs) (brasero_burn_record burn.c:2524)

Què us sembla que podria fer?

Gràcies a la bestreta,

Joan Inglada

---

### Post by jinglada on 2009-02-18
> **jinglada said:**
> Session error : no es pot bloquejar la unitat (procés d'enregistrament en curs) (brasero_burn_record burn.c:2524)

He desinstal·lat i re-instal·lat l'aplicació i ja grava aparentment bé.

En acabar, quan ha fet la prova d'integritat, dóna Checksum error:

Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_start_progress
BraseroChecksumFiles Called brasero_job_set_progress (0,001972)

.......

BraseroChecksumFiles Called brasero_job_set_progress (1,000000)
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_last_session_address
BraseroChecksumFiles called brasero_job_get_device
BraseroChecksumFiles Found file 
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_FEK7OU.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles finished track successfully
BraseroChecksumFiles stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-speed=8
	-M
	/dev/scd0
	-dry-run
	-r
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_LCPNPU
	-exclude-list
	/tmp/brasero_tmp_SAPNPU
	-print-size
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -C 1287728,1325152 -M /dev/fd/3 -r -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_LCPNPU -exclude-list /tmp/brasero_tmp_SAPNPU -print-size | builtin_dd of=/dev/scd0 obs=32k seek=82822'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Rock Ridge signatures found

................

BraseroGrowisofs stderr: Total extents scheduled to be written = 25299
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_data_label
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-speed=8
	-use-the-force-luke=tracksize:25299
	-M
	/dev/scd0
	-r
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_5CKIPU
	-exclude-list
	/tmp/brasero_tmp_IXLIPU
	-V
	docs-a-protegir-(17 feb 09)
	-A
	Brasero-0.8.2
	-sysid
	LINUX
	-v
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -C 1287728,1325152 -M /dev/fd/3 -r -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_5CKIPU -exclude-list /tmp/brasero_tmp_IXLIPU -V docs-a-protegir-(17 feb 09) -A Brasero-0.8.2 -sysid LINUX -v | builtin_dd of=/dev/scd0 obs=32k seek=82822'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: genisoimage 1.1.8 (Linux)
BraseroGrowisofs stderr: Rock Ridge signatures found
BraseroGrowisofs stderr: Scanning /media/dades/documents a protegir/rb

......

BraseroGrowisofs stderr: Writing:   Initial Padblock                        Start Block 1325152
BraseroGrowisofs stderr: Done with: Initial Padblock                        Block(s)    16
BraseroGrowisofs stderr: Writing:   Primary Volume Descriptor               Start Block 1325168
BraseroGrowisofs stderr: Done with: Primary Volume Descriptor               Block(s)    1
BraseroGrowisofs stderr: Writing:   End Volume Descriptor                   Start Block 1325169
BraseroGrowisofs stderr: Done with: End Volume Descriptor                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Version block                           Start Block 1325170
BraseroGrowisofs stderr: Done with: Version block                           Block(s)    1
BraseroGrowisofs stderr: Writing:   Path table                              Start Block 1325171
BraseroGrowisofs stderr: Done with: Path table                              Block(s)    4
BraseroGrowisofs stderr: Writing:   Directory tree                          Start Block 1325175
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    318
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 1325493
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 1325493
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 1325494
BraseroGrowisofs stderr:  98.49% done, estimate finish Wed Feb 18 10:25:10 2009
BraseroGrowisofs Called brasero_job_set_progress (0,984900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  98.86% done, estimate finish Wed Feb 18 10:25:10 2009
BraseroGrowisofs Called brasero_job_set_progress (0,988600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  99.23% done, estimate finish Wed Feb 18 10:25:10 2009
BraseroGrowisofs Called brasero_job_set_progress (0,992300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 8.2x1352KBps.
BraseroGrowisofs stderr:  99.60% done, estimate finish Wed Feb 18 10:25:27 2009
BraseroGrowisofs Called brasero_job_set_progress (0,996000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  99.97% done, estimate finish Wed Feb 18 10:25:28 2009
BraseroGrowisofs Called brasero_job_set_progress (0,999700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: Total translation table size: 0
BraseroGrowisofs stderr: Total rockridge attributes bytes: 293083
BraseroGrowisofs stderr: Total directory bytes: 632832
BraseroGrowisofs stderr: Path table size(bytes): 2502
BraseroGrowisofs stderr: Done with: The File(s)                             Block(s)    24807
BraseroGrowisofs stderr: Writing:   Ending Padblock                         Start Block 1350301
BraseroGrowisofs stderr: Done with: Ending Padblock                         Block(s)    150
BraseroGrowisofs stderr: Max brk space used 236000
BraseroGrowisofs stderr: 1350451 extents written (2637 MB)
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs Called brasero_job_set_progress (1,000000)
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/scd0: closing track
BraseroGrowisofs stderr: /dev/scd0: closing session
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 0
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_start_progress
BraseroChecksumFiles Called brasero_job_set_progress (0,000358)
BraseroChecksumFiles comparing checksums for file /media/cdrom0/rb/Hayek's_'The_Road_to_Serfdom'_in_.mov : 83cd02dabe794706d6dae69aa5af6fd2 (from md5 file) / 83cd02dabe794706d6dae69aa5af6fd2 (current)
BraseroChecksumFiles Called brasero_job_set_progress (0,000716)

...
BraseroChecksumFiles called brasero_job_error
BraseroChecksumFiles finished with an error
BraseroChecksumFiles asked to stop because of an error
	error		= 22
	message	= "Alguns fitxers poden estar malmesos al disc"
BraseroChecksumFiles stopping
Session error : Alguns fitxers poden estar malmesos al disc (brasero_burn_record burn.c:2524)
---------------------------

Tanmateix he obert el DVD i puc llegir/veure/reproduir els arxius gravats que he provat. 

:(

---

### Post by jinglada on 2009-02-21
És que ningú fa servir el brasero?

---

### Post by SiscoGarcia on 2009-02-22
> **jinglada said:**
> És que ningú fa servir el brasero?

Això no ho sé, però sembla que ningú sap com ajudar-te... de moment.

Tinguis [paciència]("http://ubuntuforums.org/showthread.php?t=599965")(punt 11) ;)

---

