---
title: "DVD burning not working"
date: 2010-01-30
forum: Apple Hardware Users
---

### Post by luigi.viggiano on 2010-01-30
Hi.

trying to burn an ubuntu image into my dvd (macbook pro 5.1) I get following errors on /var/log/syslog:

```
Jan 30 21:36:24 hal9000 kernel: [ 4665.557672] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 30 21:36:24 hal9000 kernel: [ 4665.557680] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 30 21:36:24 hal9000 kernel: [ 4665.557685] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
Jan 30 21:36:24 hal9000 kernel: [ 4665.557691] end_request: I/O error, dev sr0, sector 0
Jan 30 21:36:24 hal9000 kernel: [ 4665.557697] Buffer I/O error on device sr0, logical block 0
Jan 30 21:36:24 hal9000 kernel: [ 4665.559140] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 30 21:36:24 hal9000 kernel: [ 4665.559147] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 30 21:36:24 hal9000 kernel: [ 4665.559152] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
Jan 30 21:36:24 hal9000 kernel: [ 4665.559157] end_request: I/O error, dev sr0, sector 0
Jan 30 21:36:24 hal9000 kernel: [ 4665.559162] Buffer I/O error on device sr0, logical block 0

```and following in brasero:

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_J8SC7U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_W2SC7U.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage There is a checksum already 0
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
    growisofs
    -use-the-force-luke=notray
    -use-the-force-luke=4gms
    -speed=2
    -use-the-force-luke=tracksize:353688
    -use-the-force-luke=tty
    -Z
    /dev/sr0=/home/luigi/Downloads/iso/ubuntu-9.10-desktop-amd64.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/luigi/Downloads/iso/ubuntu-9.10-desktop-amd64.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/sr0: pre-formatting blank DVD+RW...
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 2.5x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=2h/MEDIUM NOT FORMATTED]: Wrong medium type
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: :-( media is not formatted or unsupported.
BraseroGrowisofs stderr: :-( write failed: Wrong medium type
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 124
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)

```I tried a cd-rw and a dvd+rw with same unsuccessful result.

I also tried to burn the dvd with wodim with bad result. 

Any hint? (I am going to restart in OSX, but I was just planning to remove the partition...)


**update:** I tried with a dvd+r and it seems it is burning.

---

### Post by llamabr on 2010-01-30
so it's a hardware problem?  What command do you use to start the burn?

---

