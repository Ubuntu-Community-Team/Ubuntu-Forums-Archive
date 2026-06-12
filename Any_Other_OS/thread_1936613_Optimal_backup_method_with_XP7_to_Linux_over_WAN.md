---
title: "Optimal backup method with XP/7 to Linux over WAN?"
date: 2012-03-06
forum: Any Other OS
---

### Post by Roasted on 2012-03-06
When I lived at home, I had a file server that ran 247 running Ubuntu and Samba. It allowed everybody's documents to be synchronized to without issue. I've since moved out. I've successfully set up the Linux computers in the house (my mom uses Ubuntu only on her desktop and dual boots on her laptop) but I'm running into some confusion with the Windows systems, which is a mixture of W7 (mom's laptop) and XP (two desktops belonging to my brothers).

I'm curious what I can do to synchronize their data over. I'm planning on doing the same thing I did for the Linux system, where I copy everything to an external hard drive, copy it to my file server, then initiate the "rsync" afterwards and things go much quicker and stay up to date easily. I do use SSH authentication with the Linux systems, which is an area I don't think Windows is very fluent in. 

With all of that said, what is the easiest and most practical way to synchronize raw data from Windows clients (7 and XP) over the WAN to my file server that is Linux based?

---

### Post by mips on 2012-03-06
Not directly related to your question but if I can give you some advice have a look at [ClearOS]("http://www.clearfoundation.com/").

It's brilliant for home or business use.

---

### Post by Roasted on 2012-03-06
> **mips said:**
> Not directly related to your question but if I can give you some advice have a look at [ClearOS]("http://www.clearfoundation.com/").

It's brilliant for home or business use.

Yeah, I've used ClearOS, but I'm not sure how it really helps me. I have a server that's set up and in use. To change the OS isn't really plausible since I'm also running ZoneMinder on it for CCTV surveillance. The idea was to utilize the extra HDD space for backups with everybody else over the WAN, so I really need to keep the server "as is" and, if possible, make it work with the Windows clients over the WAN.

I'm starting to think maybe I'm asking for too much out of this. Most people who do over the WAN backups are businesses who do Linux to Linux or Windows to Windows. Am I asking for too much out of this? Or is there a simple, non headache-infatuated way of making Windows work with Linux over WAN connections? The other reason I'm thinking I might be better off getting a LAN based solution is the simple fact of speed... If one of my brothers picks up a 2 GB torrent, then he'll be pushing a 2 GB file down to my server, which will degrade their speed and mine for several hours until it's complete... perhaps the LAN method is the way to go?

Nonetheless, I'm still curious if it's even possible, even if it's not entirely optimal...

---

### Post by CharlesA on 2012-03-06
I'm not too sure how it would work. I do the opposite on my lan - Windows to linux, and I use robocopy for that, but you'd need to have something already mounted/mapped to use that.

---

### Post by Roasted on 2012-03-06
> **CharlesA said:**
> I'm not too sure how it would work. I do the opposite on my lan - Windows to linux, and I use robocopy for that, but you'd need to have something already mounted/mapped to use that.

What do you mean you do the opposite? Windows to Linux is the direction I'm trying to go as well. I also do Linux to Linux which is what works...

Also, is Robocopy W7 only or is it on XP as well? When I was doing this via LAN I would use Syncback Free to auto sync the raw data... it's likely what I'll use again if I go back to the LAN idea and put a box in their basement that runs 247... which is likely what I'm going to do if there's no hope for Windows-to-Linux-over-WAN backup solutions...

---

### Post by CharlesA on 2012-03-06
Ah I misread. I was thinking Linux to Windows.

I've used robocopy on WinXP but I had to download it from microsoft. It's included in Vista and 7. I've got Samba setup on my server and have a drive mapped on the windows machines so I can back documents and whatnot to that mapped drive via a scheduled task.

The big one I was thinking of was rsync over SSH, but I don't know if that will work on a Windows box.

---

### Post by CharlesA on 2012-03-06
Ah I misread. I was thinking Linux to Windows.

I've used robocopy on WinXP but I had to download it from microsoft. It's included in Vista and 7. I've got Samba setup on my server and have a drive mapped on the windows machines so I can back documents and whatnot to that mapped drive via a scheduled task.

The big one I was thinking of was rsync over SSH, but I don't know if that will work on a Windows box.

---

### Post by Roasted on 2012-03-06
> **CharlesA said:**
> Ah I misread. I was thinking Linux to Windows.

I've used robocopy on WinXP but I had to download it from microsoft. It's included in Vista and 7. I've got Samba setup on my server and have a drive mapped on the windows machines so I can back documents and whatnot to that mapped drive via a scheduled task.

The big one I was thinking of was rsync over SSH, but I don't know if that will work on a Windows box.

Yeah... the more I read about off site backups, the more I realize, people tend to stick with similar platforms. Most off site backups are server to server, so they tend to do Win to Win or Linux to Linux, etc., and understandably so.

I decided it's probably just going to be easier and more practical to rug up a spare machine I have and sit it in the basement somewhere within their residence and let it do its job. That way backups are quicker, my online-gamer brothers aren't getting hit by slower bandwidth due to days-long backups of new data, etc. I think I'll just set up DDNS on that box and forward SSH through it so I can remote in via terminal now and then and make sure things look good. It just sounds a bit too messy when you're talking mixing platforms that aren't built with the same capability. I'm sure if I was backing up W7 to W7 it would be as easy as I've experienced with Ubuntu to Ubuntu, but W7 doesn't play too nice with others, so making it work with Ubuntu is going to be a cold day in you know where... :lolflag:

---

### Post by CharlesA on 2012-03-06
That sounds like the best thing to do.

Haha. I'm just using Samba on my Ubuntu box and it's been fine for XP, Vista and 7.

---

### Post by Roasted on 2012-03-06
> **CharlesA said:**
> That sounds like the best thing to do.

Haha. I'm just using Samba on my Ubuntu box and it's been fine for XP, Vista and 7.

Yeah, Samba is pretty much awesome if you ask me. I've heard some conflicting opinions about it, how it's slow, etc. I directly compared an identical scenario with using NFS vs SMB, and SMB was definitely not slower. It was right on par with what NFS provided in my case. I love having a Linux + Samba box around. It really makes file sharing on the LAN seamless when it comes to multiple platforms. It's great for me because my girlfriend's laptop is Windows and I use a mixture of Mac and Linux for work.

When it comes to Linux clients on the LAN, I really love Deja Dup. Auto mounts Samba shares, great disaster recovery, etc. I wish Windows had something like it (maybe they do?) but for them I just use Syncback Free. It syncs raw data, so it's not a compressed incremental backup or anything, but it still gets the job done.

---

### Post by CharlesA on 2012-03-06
I think robocopy does the same thing - it copies the whole file if the file has changed instead of just the data that has changed.

I wish there was something like rsync that was native to Windows, but robocopy is as close as I have gotten.

---

### Post by mips on 2012-03-07
> **Roasted said:**
> Yeah, I've used ClearOS, but I'm not sure how it really helps me.

I'm starting to think maybe I'm asking for too much out of this.

Nonetheless, I'm still curious if it's even possible, even if it's not entirely optimal...

It doesn't, I'm just punting clearos as it makes a nice server with easy to use interface.

Not really.

Yes it's possible.


Do you (where the server is located) have a static IP address from your ISP or is it dynamic?

If you only have a dynamic IP address allocated by your ISP you will have to subscribe to a service like DynDNS or one of the many others that works with linux. This is to ensure the windows clients on the other side of the WAN always know how to connect to your servers. Your server will have a small client or daemon that will constantly update the dynamic dns server with the IP allocated by your ISP and it links that IP to a host name which you use to connect to the servers with.

As for the actual backups have a look at rsync, it is pretty efficient bandwidth wise and you can set it up to only backup files that have changed since the last backup.

Here are some links you might find useful,
[https://docs.google.com/viewer?a=v&q=cache:qdtRpfy6Z-EJ:www.backupassist.com/rsync/Setting_up_Rsync_Server.pdf+&hl=en&gl=za&pid=bl&srcid=ADGEESh1p5Hzx5AsQcBPQUhjkPkafuTN6IHQQ80KZQRG2rnZPkJE59QwIQQ6slLy-7HV0bs554DKStjgHOMzyGvYo8oCuSp_6DChjEPzAtVqlWuwRUEDUKN3Nunz2d5PkgCNhruhRQRQ&sig=AHIEtbQtHxLQTpUMU2OF18XMU4GuAPJhEw](https://docs.google.com/viewer?a=v&q=cache:qdtRpfy6Z-EJ:www.backupassist.com/rsync/Setting_up_Rsync_Server.pdf+&hl=en&gl=za&pid=bl&srcid=ADGEESh1p5Hzx5AsQcBPQUhjkPkafuTN6IHQQ80KZQRG2rnZPkJE59QwIQQ6slLy-7HV0bs554DKStjgHOMzyGvYo8oCuSp_6DChjEPzAtVqlWuwRUEDUKN3Nunz2d5PkgCNhruhRQRQ&sig=AHIEtbQtHxLQTpUMU2OF18XMU4GuAPJhEw)
[http://www.backupassist.com/BackupAssist/tour_Rsync.html](http://www.backupassist.com/BackupAssist/tour_Rsync.html)
[http://nicj.net/2012/01/04/backing-up-windows-computers-to-a-synology-nas-via-ssh-and-rsync](http://nicj.net/2012/01/04/backing-up-windows-computers-to-a-synology-nas-via-ssh-and-rsync)
[http://www.tux.org/~tbr/rsync/](http://www.tux.org/~tbr/rsync/)

Backup assist is a commercial app but I'm pretty sure you can find something similar that is freeware or opensource. The above links are just to give you some ideas and not a definitive answer to your question.

When I have some time I'll search for some decent windows rsync backup clients/GUIs.

---

### Post by mips on 2012-03-07
[http://en.wikipedia.org/wiki/Rsync#Solutions_using_Rsync](http://en.wikipedia.org/wiki/Rsync#Solutions_using_Rsync)

From that list these seem to be open source or freeware,
[http://grsync-win.sourceforge.net/](http://grsync-win.sourceforge.net/) & [http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)
[http://www.qtdtools.de/page.php?seite=QtdSync](http://www.qtdtools.de/page.php?seite=QtdSync)
[http://www.yinter.net/](http://www.yinter.net/)
[http://code.google.com/p/duplicati/](http://code.google.com/p/duplicati/)
[http://freefilesync.sourceforge.net/](http://freefilesync.sourceforge.net/)
[http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp](http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp)
[http://www.jumpingbytes.com/en/puresync.html](http://www.jumpingbytes.com/en/puresync.html)
[http://rdiff-backup.nongnu.org/](http://rdiff-backup.nongnu.org/)

You will have to look at them and evaluate the strengths & weaknesses of each one. I have grsync (first link above) installed in linux but I have not used it yet.

---

### Post by Roasted on 2012-03-07
I have a dynamic IP but I have a hostname with No-IP.com which has worked out well, so we're covered in that department. The brick wall I ran into was just getting the Windows systems to work with SSH/sync/WAN backups. It's really disappointing something more logical isn't built into Windows, but who am I kidding... 

GRsync I've used in Linux. It's a pretty simple program, mostly just hitting checkboxes that correspond to certain switches on the terminal command for -r -l -t -o -g etc. Works great though.

I'll look through some of the links you have provided, as some of these names I haven't heard of yet. Crossing fingers here! Thanks guys.

---

