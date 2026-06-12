---
title: "Reads Audio CD, but no play?"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by unoobu on 2006-05-22
I put in my new Pearl Jam album, and CD Player reads the tracks on the cd.  I press play, and it plays the tracks, but I get no audio...  When I first put it in, Sound Juicer automatically opened, and when I tried to play it there, it gave me this error:

Error playing CD.
Reason: OSS device "/dev/dsp" is already in use by another program.

Okay, but WTF?  I am not using my audio card at the time, nor am I using my cd drive!
Someone please show me how much of a noob I am and explain this error message and what I should do about it!!!  PLEASE!!!

---

### Post by unoobu on 2006-05-22
bump:  I've seen no discussion on this topic, or at least none that offers a solution...

---

### Post by user1397 on 2006-05-22
[quote=unoobu]bump:  I've seen no discussion on this topic, or at least none that offers a solution...[/quote]
you probably had another program on that was using your sound card.  just quit out of sound juicer, and open up cd player or rhythmbox or mplayer or xmms or realplayer or totem movie player or whatever program you most desire, and try playing it from there

---

### Post by unoobu on 2006-05-22
[QUOTE=erik1397]you probably had another program on that was using your sound card.  just quit out of sound juicer, and open up cd player or rhythmbox or mplayer or xmms or realplayer or totem movie player or whatever program you most desire, and try playing it from there[/QUOTE]

As I said, I am not using the audio card at the time, nor am I accessing the CD from any other program.  The CD just doesn't play.  It won't play in CD Player...  It will show the track playing, but I get no audio.  I have closed all programs but CD player and it still doesn't work.

---

### Post by ProjectGod on 2006-05-22
. uhhh does the magick "SHIFT" key work in linux? i mean when you pop a CD into the drive. and you hold down the shift key... does it by bypass the "auto - run"? i'm not sure cause i'm currenty using a windows machine ](*,) 

everytime i pop a cd into my ubuntu machine it always opens up "my computer" automatically... :???: 

[SIZE="1"]i tried listening to tool's latest album with my ubu. very poor album from a good band. :mrgreen:[/SIZE]

---

### Post by Sef on 2006-05-22
> I put in my new Pearl Jam album, and CD Player reads the tracks on the cd. I press play, and it plays the tracks, but I get no audio...

Have you installed the codecs?

[http://wiki.ubuntu.com/RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats")

---

### Post by nalmeth on 2006-05-23
Open the system monitor to see if there are task's running that are hogging the audio system.

ESD (enlightened sound daemon) tend's to be the most common interference for people, it seems. Kill the ESD processes, and you may fix the problem.

---

### Post by unoobu on 2006-05-26
[QUOTE=nalmeth]Open the system monitor to see if there are task's running that are hogging the audio system.
[/QUOTE]

Nope.  This did not fix the problem.  There was nothing taking up CPU usage.  Nothing taking up audio...  It just won't play.  The CD codec is not private, correct?  I thought CD data was universal?

Anyhow, subdiscussion:

How hard is it going to be to install Ubuntu: 6.06 - Dapper Drake?  Am I going to have to loose all of my installs and configurations?  I just got this one up and running about two weeks ago, I am not doing it all over again!  I need to remember to back up my emails, thunderbird & firefox settings and links, etc...

What is the best package installer?  Ubuntu Easy, or Automatix...  I've been using Automatix with many problems, is Easy better?  I am really not a programmer, but using Linux makes me want to learn...  I love the participation, and the sharing of ideas... the idea that thought is free.

Peace,

uNOOBu

---

### Post by crispy_420 on 2006-05-26
Just look for a thread on upgrading to Dapper, there are many. It will the first release to get support beyond 18 months, this one will be supported for 3 years (desktop) and 5 years (server).

As far as data loss, just backup your important files to be on the safe side.

If you want more software (restricted codecs, unsupported programs, etc.) just add more repositories. As a side note that will be easier in Dapper.

---

### Post by crispy_420 on 2006-05-26
Upgrade info [HERE]("http://ubuntuforums.org/showthread.php?t=182223&referrerid=0").

Looks like they will make it real easy to upgrade. Haven't tried yet but I will this weekend.

---

