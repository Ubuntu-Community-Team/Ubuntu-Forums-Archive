---
title: "Trouble ripping DVD's"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by guitarist549 on 2007-04-16
Alright, I'm having trouble ripping certain titles to my hard drive. DVD:RIP will just say that it is ripping, but the time remaining will just freeze, and the dvd drive will just make a clicking noise. I get the same problem with acidrip. I'm thinking that it has something to do with the encryption, but I'm not entirely certain. Has anyone else had this problem?

---

### Post by jdong on 2007-04-16
It sounds like the computer is having trouble reading the DVD (i.e. a scratched disc?). Check **dmesg** output. Do you see errors about unreadable sectors?

---

### Post by guitarist549 on 2007-04-16
Well I'm currently ripping another movie... but when it finishes, I'll post the dmesg.
I don't think that it's due to a scratched disk, as I have had this problem with many disks and most of them have been in near mint condition.

---

### Post by tchoklat on 2007-04-16
ripping and burning DVD's is why I have XP dualboot on my system. OneclickDVDcopy rips and burns anything easily and without problem for me.

---

### Post by stmiller on 2007-04-16
> **guitarist549 said:**
> Alright, I'm having trouble ripping certain titles to my hard drive. DVD:RIP will just say that it is ripping, but the time remaining will just freeze, and the dvd drive will just make a clicking noise. I get the same problem with acidrip. I'm thinking that it has something to do with the encryption, but I'm not entirely certain. Has anyone else had this problem?

Click the option to copy the disc to the hard drive first. On-the-fly encoding in DVD:RIP has given me problems in the past.

---

### Post by svega85 on 2007-04-27
> **stmiller said:**
> Click the option to copy the disc to the hard drive first. On-the-fly encoding in DVD:RIP has given me problems in the past.
[COLOR=Black]i have the same problem but without the clicking sound here's the dvdrip log
[/COLOR]```
[COLOR=Black]Thu Apr 26 22:37:39 2007 Detected transcode version: 10002
Thu Apr 26 22:50:13 2007 Project file saved to '/home/shawn/dvdrip/TheReturn.rip'
Thu Apr 26 22:50:13 2007 Project temporary dir '/home/shawn/dvdrip/TheReturn/tmp' created
Thu Apr 26 22:50:14 2007 Project {name} created
Thu Apr 26 22:51:16 2007 Start job 'Read TOC (lsdvd|tcprobe)'
Thu Apr 26 22:51:16 2007 Start job 'Read TOC (lsdvd)'
Thu Apr 26 22:51:16 2007 Executing command: execflow lsdvd -a -n -c -s -v -Op \/dev\/scd0 2>/dev/null && echo EXECFLOW_OK
Thu Apr 26 22:51:20 2007 Not enabling PSU core, because this movie has only one PSU.
Thu Apr 26 22:51:20 2007 Not enabling PSU core, because this movie has only one PSU.
Thu Apr 26 22:51:20 2007 Not enabling PSU core, because this movie has only one PSU.
Thu Apr 26 22:51:20 2007 Not enabling PSU core, because this movie has only one PSU.
Thu Apr 26 22:51:20 2007 Not enabling PSU core, because this movie has only one PSU.
Thu Apr 26 22:51:20 2007 Not enabling PSU core, because this movie has only one PSU.
Thu Apr 26 22:51:20 2007 Not enabling PSU core, because this movie has only one PSU.
Thu Apr 26 22:51:20 2007 Not enabling PSU core, because this movie has only one PSU.
Thu Apr 26 22:51:20 2007 Start job 'Read TOC (tcprobe)'
Thu Apr 26 22:51:20 2007 Successfully read DVD TOC
Thu Apr 26 22:51:20 2007 Copying IFO files from /media/cdrom0 to /home/shawn/dvdrip/TheReturn/tmp/ifo
Thu Apr 26 22:51:21 2007 Job 'Read TOC (lsdvd|tcprobe)' finished
Thu Apr 26 22:51:21 2007 Job 'Read TOC (tcprobe)' finished
Thu Apr 26 22:51:21 2007 Job 'Read TOC (lsdvd)' finished
Thu Apr 26 22:53:11 2007 Start job 'Rip selected title(s) / chapter(s)'
Thu Apr 26 22:53:11 2007 Start job 'Process title #1'
[/COLOR][COLOR=Black]Thu Apr 26 22:53:11 2007 Start job 'Rip - title #1'
Thu Apr 26 22:53:11 2007 Executing command: rm -f /home/shawn/dvdrip/TheReturn/vob/001//TheReturn-???.vob && execflow -n 19 tccat -t dvd -T 1,-1,1 -i \/dev\/scd0 | dvdrip-splitpipe -f /home/shawn/dvdrip/TheReturn/tmp/TheReturn-001-nav.log 1024 /home/shawn/dvdrip/TheReturn/vob/001//TheReturn vob  | tcextract -a 0 -x ac3 -t vob | tcdecode -x ac3 | tcscan -x pcm && echo EXECFLOW_OK
Thu Apr 26 22:53:15 2007 Executing command: execflow tcprobe  -i /home/shawn/dvdrip/TheReturn/vob/001/ && echo EXECFLOW_OK
Thu Apr 26 22:53:15 2007 Job 'Rip - title #1' finished
Thu Apr 26 23:01:17 2007 Rip selected title(s) / chapter(s): 20% done.
Thu Apr 26 23:01:17 2007 Process title #1: 20% done.
[/COLOR]
```

---

### Post by stmiller on 2007-04-27
Do you have libdvdcss2 installed?

---

### Post by svega85 on 2007-04-27
ok i figured it out i didn't have libdvdcss2 and it's not in synaptic so you have to install libdvdread3 then run ```
sudo sh /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by stchman on 2007-05-08
> **guitarist549 said:**
> Alright, I'm having trouble ripping certain titles to my hard drive. DVD:RIP will just say that it is ripping, but the time remaining will just freeze, and the dvd drive will just make a clicking noise. I get the same problem with acidrip. I'm thinking that it has something to do with the encryption, but I'm not entirely certain. Has anyone else had this problem?

I have a procedure to download the codecs and configure k9copy to rip your DVDs to a .iso file. You will need to install the medibuntu codecs and the CSS decoder to play encrypted DVDs.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

It works for many DVDs, but some newer DVDs it won't work.

---

### Post by Alterax on 2007-06-07
The clicking noise may indicate that the mechanism that moves the laser may be broken or out of alignment.  If it does this with most of them, or gets worse, then your best bet would be to get a new drive.

--Alterax

---

