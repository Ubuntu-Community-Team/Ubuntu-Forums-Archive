---
title: "Unknown program not responding"
date: 2014-01-28
forum: Any Other OS
---

### Post by CrzPW74 on 2014-01-28
I am using pinguy os based on ubuntu 12.04, kernel 3.2.0-25, gnome 3.4.1. I recently noticed that when I shut down my laptop, I get a message of an unresposive program. The message says the program is unknown. The only vchanges I made to laptop were adding Redbook journal, added kOrganiser, added Filezilla..  I tried this post info [http://ubuntuforums.org/showthread.php?t=2069929](http://ubuntuforums.org/showthread.php?t=2069929) and put gedit **/etc/rsyslog.d/50-default.conf**. into the terminal, this brought up the file BUT i could not save,  but got permission denied when I tried. Any ideas , help, suggestions would be greatly appreciated Thanx

---

### Post by bashiergui on 2014-01-28
Yeah you would get permission denied because you need to use gksudo to modify something owned by root.

Start with /var/log/messages to see what application is hanging.

---

### Post by CrzPW74 on 2014-01-28
Thank you so much. I was able to open, edit and save the file. Now I need to shut down and see what happens. So though there is nothing in the var/logs/messages=0bytes. ANyway going to shut down now and see. Thank you

---

### Post by CrzPW74 on 2014-01-29
Hello again,
I rebooted the laptop twice and saved the last section of the "messages" file, but I dont really know what I am looking (or doing for that matter lol).Here is the last portion of the file from when I rebooted.

  	 	 	 	   

 [COLOR=#0000ff]**This is first try last of the lines.**[/COLOR]
 

 

 Jan 28 22:58:37 Ravns-nest kernel: [   21.689883] type=1400 audit(1390971517.240:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1263 comm="apparmor_parser"
 Jan 28 22:58:37 Ravns-nest kernel: [   21.723037] ADDRCONF(NETDEV_UP): eth0: link is not ready
 Jan 28 22:58:37 Ravns-nest kernel: [   21.725054] ADDRCONF(NETDEV_UP): eth0: link is not ready
 Jan 28 22:58:37 Ravns-nest kernel: [   21.730231] ppdev: user-space parallel port driver
 Jan 28 22:58:37 Ravns-nest kernel: [   22.098285] Cannot change disksize for initialized device
 Jan 28 22:58:37 Ravns-nest kernel: [   22.118016] init: zramswap pre-start process (1377) terminated with status 1
 Jan 28 22:58:37 Ravns-nest kernel: [   22.134207] init: zramswap post-stop process (1428) terminated with status 255
 Jan 28 22:58:37 Ravns-nest kernel: [   22.269105] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
 Jan 28 22:58:37 Ravns-nest kernel: [   22.300152] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
 Jan 28 22:58:38 Ravns-nest kernel: [   22.706805] tg3 0000:02:00.0: eth0: Link is down
 Jan 28 22:58:38 Ravns-nest kernel: [   23.335520] init: plymouth-stop pre-start process (1796) terminated with status 1
 Jan 28 22:59:18 Ravns-nest nautilus: [N-A] Nautilus-Actions Tracker 3.2.2 initializing...
 Jan 28 22:59:18 Ravns-nest nautilus: [N-A] Nautilus-Actions Menu Extender 3.2.2 initializing...
 Jan 28 22:59:21 Ravns-nest kernel: [   66.130693] audit_printk_skb: 39 callbacks suppressed
 Jan 28 22:59:21 Ravns-nest kernel: [   66.130697] type=1400 audit(1390971561.718:25): apparmor="DENIED" operation="open" parent=3097 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=3098 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
 

 

 

 [COLOR=#0000ff]**This is shut down at 11:09 pm and reboot also shows lines fron b4 reboot**[/COLOR]
 

 

 an 28 22:59:18 Ravns-nest nautilus: [N-A] Nautilus-Actions Menu Extender 3.2.2 initializing... 
 Jan 28 22:59:21 Ravns-nest kernel: [   66.130693] audit_printk_skb: 39 callbacks suppressed 
 Jan 28 22:59:21 Ravns-nest kernel: [   66.130697] type=1400 audit(1390971561.718:25): apparmor="DENIED" operation="open" parent=3097 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=3098 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0 
 Jan 28 23:11:20 Ravns-nest kernel: Kernel logging (proc) stopped. 
 Jan 28 23:11:20 Ravns-nest rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1208" x-info="http://www.rsyslog.com"] exiting on signal 15.
  I have NO IDEA  hopefully you can help. Thanx

---

### Post by bashiergui on 2014-01-29
Applications can log to /var/log/messages but they aren't required to. Each application can log whereever the developer choses. So if you're trying to figure out what program is hanging at shutdown, then you might have to look at /messages and syslogs. I have no idea what the log entry that you're looking for would look like, though.

This isn't a security issue so let's see if you do better in a more general forum.

---

### Post by oldos2er on 2014-01-29
Moved to Other OS/Distro Support.

---

### Post by CrzPW74 on 2014-01-30
Ok, and thank you for the help. I had scanned the different file in thelogs folder including message and syslog, but there is so much there I just am not sure what to look for. I try to look at the time stamp from when I shut dowm the laptop down, and see if there is anytihng that says "warning" or "error" but so far I cant  make heads or tails of this lol...I may just have to un install each app and see if that works.
Well thanks again.

---

### Post by CrzPW74 on 2014-01-30
I am tahnkful for the help and it turns out I have solved the problem. I was unable to locate anything that made sense inthe log files so,  simply started uninstalling. It turns outs that the unidentified program had to be either kOrgarganiser or Filezilla. I foolishly uninstall kOrg frist and hit reboot. When I saw the error message again I cancelled and went back and uninstalled FileZilla, however I got the same mesage again but this time I let it shutdown. I should have done that when I uninstalled kOrg. Anyway the good news is no more hanging program YAY!!!!:D:D

---

