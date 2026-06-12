---
title: "Sound card does not work properly under Ubuntu, worked fine under Kubuntu"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by mikewave on 2007-01-07
When using any audio or video application, sound ONLY comes from the left channel. I have checked all connections and all sound hardware (a SONY stereo receiver with two Minimus-7 loudspeakers). Everything is normal.

My sound card is an M-Audio Delta 410.

With a previous installation of KUBUNTU linux, the sound card performed normally.

This computer uses one of two IDE hard drives, both of which are in removable plastic caddies, one containing Ubuntu Linux, the other containing Windows 98SE. IOW, when one HD is inserted, the box is a Linux box, when the other one is put in place, the box is a Windows 98SE box.

When the WIN98SE HD is put in place, the sound card performs normally.

The last time I installed updates to Ubuntu Linux was on 4-JAN-07.

Platform  	1 Ghz PIII, 256 MB of RAM, 80 GB HD
Ubuntu Linux (Gnome)(Dapper Drake?)
OS Version 	6.06 LTS

---

### Post by houstonbofh on 2007-01-07
> **mikewave said:**
> When using any audio or video application, sound ONLY comes from the left channel. I have checked all connections and all sound hardware (a SONY stereo receiver with two Minimus-7 loudspeakers). Everything is normal.

My sound card is an M-Audio Delta 410.

With a previous installation of KUBUNTU linux, the sound card performed normally.

This computer uses one of two IDE hard drives, both of which are in removable plastic caddies, one containing Ubuntu Linux, the other containing Windows 98SE. IOW, when one HD is inserted, the box is a Linux box, when the other one is put in place, the box is a Windows 98SE box.

When the WIN98SE HD is put in place, the sound card performs normally.

The last time I installed updates to Ubuntu Linux was on 4-JAN-07.

Platform  	1 Ghz PIII, 256 MB of RAM, 80 GB HD
Ubuntu Linux (Gnome)(Dapper Drake?)
OS Version 	6.06 LTS
And the sound card is?  Which driver are you trying to output to?  Does it do it in ALSA and OSS, or just one?

---

### Post by louieb on 2007-01-07
I think its Gnome. My first Linux distro was FC5 (Gnome desktop). Sound worked for a few days the just quit one day. For some reason thought to heck with Fedora and installed Ubuntu same thing sound worked for a few days then it stopped working in Gnome. But in KDE (Kubuntu-desktop) sound applications worked just fine. Being to lazy to fix Gnomes sound issues  I still use Gnome for my desktop but I use KDE sound applications inside of Gnome. Works just fine for me.

---

### Post by mikewave on 2007-01-07
I got rid of Kubuntu because updates and installations were much more difficult than under the Gnome-based version. I also am using a book on the fundamentals of Ubuntu and it doesn't cover Kubuntu.

So, which sound drivers or other files should I install and/or rip out?

---

### Post by mikewave on 2007-01-07
> **houstonbofh said:**
> And the sound card is?  Which driver are you trying to output to?  Does it do it in ALSA and OSS, or just one?

As I said in my original post, it is an M-Audio Delta 410.

How do I set the sound card for the appropriate driver? I cannot find the appaopriate control-panel entry. Is this a command-line function?

---

### Post by houstonbofh on 2007-01-08
> **mikewave said:**
> As I said in my original post, it is an M-Audio Delta 410.

How do I set the sound card for the appropriate driver? I cannot find the appaopriate control-panel entry. Is this a command-line function?
Sorry...  I missed it.  Need sleep.

Anyway, right click on the speaker in the top right taskbar, and go to preferences.  The first dropdown should give both ALSA and OSS.  ALSA is better, but only if it works. ;)  Also in the top taskbar, go to System --> Preferences --> Sound.  Most things are set to autodetect.  Try the other settings and see if you get a change.

And all this with no keyboard, for your pleasure. :mrgreen:

---

### Post by Patrick K on 2007-01-08
Do you have the ALSA ice1712 driver installed? If not, here is the link:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=Delta+410.&chip=ICE1712+%28Envy24%29&module=ice1712](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=Delta+410.&chip=ICE1712+%28Envy24%29&module=ice1712)

---

