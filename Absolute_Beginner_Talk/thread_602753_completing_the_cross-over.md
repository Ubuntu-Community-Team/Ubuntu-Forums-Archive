---
title: "completing the cross-over"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by sentient.being on 2007-11-04
Hi
I have finally decided to say farewell to MS Win and migrate to Ubuntu full-time. I have spend long hours trying to fix various tids n bits which though tedious has been a satisfying xp(!)rience. However some stuff are still eluding me. I hope someone could help me -

1. I am unable to run .rm files no matter what. I installed mplayer (and xine too). I downladed the binaries from the mplayer site but am unable to install them.(it names some folders which dont even exist on the system)

2. how do i get on my college LAN network? On windows we used oDC or DC++. I installed linuxDC++ and it does connect but is refusing to download any files.

3. My hostel internet connection is practically non existent. can i download the various packages and dependencies in the main lab and bring them on my desktop? how do i know the dependencies while in the lab?

4. Which IDE is best for C/C++? I want to start OpenGL and sockets programming. What other packages should i download?(Some tutorials would also be helpful)

5. While we are there, is there any way to increase the internet speed on my comp through linux( hacking etc) ?

6. how often should i upgrade my ubuntu? if i have feisty fawn, should i upgrade to gutsy gibbon?(my connection is slow after all)

i use ubuntu 7.04 on an amd64 x2 processor.
thanks for your help.

---

### Post by HermanAB on 2007-11-04
1.  No idea what a .rm file is.  On Linux files are generally identified by a program called 'file' and it doesn't care what the name is, it looks at the contents of the file.  So any file can have any name.  The .ext means nothing.
2. Try dhclient
3. It sounds like you should rather get a CDROM/DVD distribution such as Fedora, Suse or Mandriva.
4. Try Glade with GTK2+
5. Speed depends on many factors.  There is no magical pixiedust, but most 'slowness' is caused by bad DNS.  Investigte the DNS using 'dig', then put the fastest DNS at the top in /etc/resolv.conf.
6. Once a week is paranoid and will likely cause more trouble than it fix. Once a year is sufficient.  Once in 5 years is a bit extreme.

Cheers,

Herman

---

### Post by discmaster on 2007-11-04
rm file is  Real Media; [Real Player 10 for Linux]("http://www.real.com/linux/") will play those. :)

---

