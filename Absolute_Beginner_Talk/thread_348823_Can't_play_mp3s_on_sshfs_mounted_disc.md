---
title: "Can't play mp3s on sshfs mounted disc"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by albesan on 2007-01-29
Not sure what it was that got it fixed but it is working now.
The problem was:

hello team,

I CAN mount/access/browse the files normally. I CAN add the directory to Listen media player; it CAN see the files, filenames etc but when I try to play it behaves like the volume is missing, running through all the titles and generating all the notification windows with the track info in a long series of windows poping upwards really fast but not playing anything and not responding to any input.
All I can do is force a log out.

Have you guys/girls come across this kind of behaviour? Any guidance on how to diagnose/cure this would be really appreciated.

I'm using Dapper (ubuntu) on a Dell inspiron. The server (all of this is over the home lan) is running Dapper (xubuntu) on a ppc. 

a.

---

### Post by albesan on 2007-01-30
anybody?

---

### Post by albesan on 2007-02-02
sorry, bumping it again.

---

### Post by mongooseman1128 on 2007-02-02
have you checked the volume control for ubuntu and the program? also, you can make sure it's not the speakers by plugging headphones directly into the speaker port on the PC

---

### Post by kebes on 2007-02-02
This is going to sound stupid, but do you have mp3 support installed? I mean, can you play local mp3 files?

Remember that mp3 support isn't installed by default in Ubuntu. You have to add it after the installation. You can use [automatix]("http://www.getautomatix.com/") to quickly add mp3, DVD, video codecs and other "must have" software.

The reason I'm suggesting this is because the behavior you describe (scanning through the files in quick succession, but not playing anything) is exaclty what happens when support for the given audio type is not present.


If that's not the problem (you do have mp3 support), try manually copying a file to your local computer and playing it from there. See if there is some problem with the file transfer over the sshfs mount.

---

### Post by mongooseman1128 on 2007-02-03
he must have mp3 support installed, if he didn't then the player would simply give a message that the file type isn't supported

---

### Post by albesan on 2007-02-03
hey, finally some help... thanks a lot for your replies...

Yes, mp3 files play locally without a problem.
Transfering files through sshfs works very well as well.

I'm also streaming files from the server using gnump3d and also works seamlessly, I'm actually quite impressed about how everything works when I take in consideration how little I know about linux.

In the back of my mind I'm wondering whether it might have something to do with the formating of the external drive where the mp3 files are.

Would I need to use an specific formating for that to work better or at all?

Also, in this kind of setup, when playing mp3's over sshfs, does the server need something I might be missing?

Thanks again for your help.


a.

---

### Post by olejorgen on 2007-02-03
Hi, you're using sshfs, not the built in ssh support in natilus, (ssh://...) right?

Can you play it with somthing else? (mplayer, totem, etc..)

I checked with mplayer and totem here, and it works.

My sshfs version is 1.7 (I think this is a newer version than the repos have)

> Also, in this kind of setup, when playing mp3's over sshfs, does the server need something I might be missing?
If I understand things correctly, no. Everything should be transparent, except maybe symlinks.

---

### Post by albesan on 2007-02-03
hello all, and thanks for your replies.

It is working now, although a bit jerky.

I would like to be able to post the solution but I don't know what did I do to make it work as I haven't done anything!!

Thanks to all for your time/attention/help.

I suspect it must have been a system update that fixed it, because I haven't done anything else.

I followed olejorgen's (gracias y Ole) advice and tried mplayer to access the files and it worked. Then I thought if mplayer can any other player should be able to and tried the Exaile player which is the one I really wanted to use and it is working now...

Before today I tried, with Listen media player, Amarok, vlc, mplayer, and none of them worked.

Thanks again everybody.

a.

---

