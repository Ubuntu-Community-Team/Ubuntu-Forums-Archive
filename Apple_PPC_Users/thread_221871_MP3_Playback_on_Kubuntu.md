---
title: "MP3 Playback on Kubuntu?"
date: 2006-07-24
forum: Apple PPC Users
---

### Post by TDave on 2006-07-24
All

After following the guide in the Wiki and installing the extracodecs package, I'm still receiving no MP3 playback functionality in amarok, xmms, or kaffeine.

They will, however, play in VLC.

Am i missing something here and left out a stupidly obvious step?

Thanks

---

### Post by wieman01 on 2006-07-24
You need to install "xine" and enable the "xine" plugin in Amarok. That done, it should work.

Since you are a Mac user I am not sure if this link works for you:

[http://www.ehomeupgrade.com/entry/2663/how-to_get_full]("http://www.ehomeupgrade.com/entry/2663/how-to_get_full")

---

### Post by TDave on 2006-07-24
Thanks for the quick reply but unfortunately that doesn't seem to be the issue.

Xine is already installed and up to date and amarok has been using it since installation.

Is there any possibility that I could have installed other packages or libraries that would break/conflict with libxine-extracodecs?

Many thanks

---

### Post by wieman01 on 2006-07-24
Hi Dave, 

Have you had sound at all? Could be the volume. Don't laugh but a couple of users have had similar issues which were resolved by "unmuting" the soundcard using the terminal tool "alsamixer".

But if you definitely have sound - which I believe - try the link I have posted in here. If that does not work, then I'll have to check tonight when I am in front of my own (Ubuntu) PC.

---

### Post by TDave on 2006-07-25
wieman01

Thanks, but yep, I definitely had the volume sorted, the oggs played fine, as did various other files (mpegs, avi, even mov), it was just MP3 I was struggling with.

Saying that, however, I now have my MP3s playing back to me through amarok without knowingly changing anything.

Could have perhaps been to do with something I've updated or inadvertently removed if I installed an extra app by mistake that broke things, but I'm not too sure.

Thanks for your time though!

---

