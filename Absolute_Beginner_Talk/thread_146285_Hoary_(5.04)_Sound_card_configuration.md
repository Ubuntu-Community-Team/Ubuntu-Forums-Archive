---
title: "Hoary (5.04) Sound card configuration"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by senthil on 2006-03-18
Hello,
I am not able to configure or play sound in Ubuntu 5.04 (Hoary Hedgehog).

I have also searched the ubuntuforums but nothing seems to work for me. I have searched the internet and found some useful links:
[http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639) 
I have done the steps that are given in the above site. But still nothing works. 

If I try to play an mp3 then Xmms complains that sound card is not configured properly, and suggests to check if other applications are using the device. 

Here is the output of lspci | grep -i audio

0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

Can anyone please suggest me what I should do ?

Thanks in advance,

Senthil

---

### Post by akudewan on 2006-03-18
Try the command "killall esd" and then try to run xmms. Use sudo if there are permission issues with the command

---

### Post by senthil on 2006-03-18
Hi,
xmms when run as sudo xmms does play the mp3 but i am not able to hear any sound. When xmms is opened without sudo it gives the following error:

senthil@ubuntu:~$ xmms

Gdk-WARNING **: locale not supported by Xlib, locale set to C
libmikmod.so.2: cannot open shared object file: No such file or directory

** WARNING **: oss_open(): Failed to open audio device (/dev/dsp): Permission denied

Senthil

---

### Post by akudewan on 2006-03-18
Oops, sorry, I wasn't clear. I did not mean "sudo xmms", I meant "sudo killall esd".

If you have already tried this then run this command:
```

sudo lsof /dev/snd/*

```

This will give you an output on the screen, that will show all programs currently running that are dealing with sound. Copy paste the output here, maybe there is some program hogging up the soundcard.

---

### Post by jam'ez on 2006-03-18
i got the same problem. really annoying!!! 
the only thing i dont like on my linux at moment. love everything else!!!

---

