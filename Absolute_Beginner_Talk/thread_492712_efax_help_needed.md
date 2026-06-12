---
title: "efax help needed"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by chedog on 2007-07-05
I have efax running. It will recieve faxes no problems, but i cannot get it to recieve faxes.
here is the error log.any help please

efax: Thu Jul  5 12:12:29 2007 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 12:29 compiled Jun 21 2006 04:57:11
efax: 12:29 TIFF version 4.2 file (little-endian)
efax: 12:29 TIFF directory at 8 with 20 tags, last image.
efax: 12:29 page 1 : /tmp/kde-che/kghostviewvZsdia.ps.001 + 338 : 1728x2292 @ 204x196 dpi TIFF/FAX
efax: 12:29 argv[0]=efax
efax: 12:29 argv[1]=-v
efax: 12:29 argv[2]=ewin
efax: 12:29 argv[3]=-v
efax: 12:29 argv[4]=chewmainrxtf
efax: 12:29 argv[5]=-d/dev/ttyS0
efax: 12:29 argv[6]=-x
efax: 12:29 argv[7]=/var/lock/LCK..ttyS0
efax: 12:29 argv[8]=-iZ
efax: 12:29 argv[9]=-i&FE&D2S7=120
efax: 12:29 argv[10]=-i&C0
efax: 12:29 argv[11]=-iM1L0
efax: 12:29 argv[12]=-l
efax: 12:29 argv[13]=+1 800 555 5555
efax: 12:29 argv[14]=-kZ
efax: 12:29 argv[15]=-h
efax: 12:29 argv[16]=2007/07/05 12:12 +1 800 555 5555 che p. %d/%d
efax: 12:29 argv[17]=-t
efax: 12:29 argv[18]=T50236535
efax: 12:29 argv[19]=/tmp/kde-che/kghostviewvZsdia.ps.001
efax: 12:29 created text lock file /var/lock/LCK..ttyS0
efax: 12:29 opened /dev/ttyS0
efax: 12:29 command  "Q0V1"
efax: 12:29 waiting 2.0 s
efax: 12:29 .369 [<CR><LF>OK<CR><LF>]
efax: 12:29 response "OK"
efax: 12:29 command  "Z"
efax: 12:29 waiting 5.0 s
efax: 12:29 .689 [<CR><LF>OK<CR><LF>]
efax: 12:29 response "OK"
efax: 12:29 command  "&FE&D2S7=120"
efax: 12:29 waiting 5.0 s
efax: 12:29 .797 [AT&FE&D2S7=120<CR><CR><LF>]
efax: 12:29 .997 [OK<CR><LF>]
efax: 12:29 response "OK"
efax: 12:30 command  "&C0"
efax: 12:30 waiting 5.0 s
efax: 12:30 .289 [<CR><LF>OK<CR><LF>]
efax: 12:30 response "OK"
efax: 12:30 command  "M1L0"
efax: 12:30 waiting 5.0 s
efax: 12:30 .581 [<CR><LF>OK<CR><LF>]
efax: 12:30 response "OK"
efax: 12:30 command  "E0"
efax: 12:30 waiting 5.0 s
efax: 12:30 .873 [<CR><LF>OK<CR><LF>]
efax: 12:30 response "OK"
efax: 12:30 command  "I3"
efax: 12:30 waiting 5.0 s
efax: 12:31 .165 [<CR><LF>DAVICOM V.90 DATA/FAX/VOICE/SPEAKERPHONE MODEM,Ver:1.06N<CR><LF>]
efax: 12:31 .193 [<CR><LF>OK<CR><LF>]
efax: 12:31 response "OK"
efax: 12:31 command  "+FCLASS=?"
efax: 12:31 waiting 5.0 s
efax: 12:31 .497 [<CR><LF>0,1,8<CR><LF>]
efax: 12:31 .501 [<CR><LF>OK<CR><LF>]
efax: 12:31 response "OK"
efax: 12:31 command  "+FCLASS=1"
efax: 12:31 waiting 5.0 s
efax: 12:31 .809 [<CR><LF>OK<CR><LF>]
efax: 12:31 response "OK"
efax: 12:31 using DAVICOM V.90 DATA/FAX/VOICE/SPEAKERPHONE MODEM,Ver:1.06N in class 1
efax: 12:31 command  "+FTM=?"
efax: 12:31 waiting 5.0 s
efax: 12:32 .101 [<CR><LF>24,48,72,73,74,96,97,98,121,122,145,146<CR><LF>]
efax: 12:32 .121 [<CR><LF>OK<CR><LF>]
efax: 12:32 response "OK"
efax: 12:32 dialing T50236535
efax: 12:32 command  "DT50236535"
efax: 12:32 waiting 120.0 s
efax: 14:32 Error: dial command failed
efax: 14:32 failed -> /tmp/kde-che/kghostviewvZsdia.ps.001
efax: 14:32 command  "Q0V1"
efax: 14:32 waiting 2.0 s
efax: 14:32 .250 [<CR><LF>NO CARRIER<CR><LF>]
efax: 14:32 response "NO CARRIER"
efax: 14:32 waiting 2.0 s
efax: 14:34 command  "Q0V1"
efax: 14:34 waiting 2.0 s
efax: 14:34 .542 [<CR><LF>OK<CR><LF>]
efax: 14:34 response "OK"
efax: 14:34 command  "Z"
efax: 14:34 waiting 5.0 s
efax: 14:34 .858 [<CR><LF>OK<CR><LF>]
efax: 14:34 response "OK"
efax: 14:34 done, returning 2 (unrecoverable error)

---

### Post by houstonbofh on 2007-07-05
Do you know if your modem works otherwise?

---

### Post by chedog on 2007-07-05
only using it for faxing. will recieve faxes. not send. it rings the other end but won't do the handshake.

---

