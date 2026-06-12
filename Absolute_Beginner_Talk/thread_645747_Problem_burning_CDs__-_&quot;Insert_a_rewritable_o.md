---
title: "Problem burning CDs  - &quot;Insert a rewritable or blank CD&quot; (again?!)"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Job Atkinson on 2007-12-20
hey helpful people, 

I'm fairly novice with all this but so far have had very few problems switching from windows to Ubuntu. I'm using Gutsy Gibbon 7.10 and I like it very much. 

I have, however, one rather annoying problem.  I have been trying to burn CDs and keep getting the "Insert a rewritable or blank CD" box - and yes I have installed a blank or rewritable CD.  Any clues as too what I can do to make the thing burn them?

It was working under windows so I don't think it is a hardware problem.  I have been trying to burn through  both Rythmbox and the CD/DVD creator folder. 

cheers,

---

### Post by philinux on 2007-12-20
I've always used k3b. It's in synaptic.

Very capable piece of software.

---

### Post by Bartender on 2007-12-20
Also brasero.
If all of those programs fail to see a CD in the drive, then maybe the next thing to try is a different drive.

---

### Post by Darkade on 2007-12-20
I have the same problem. I can read CD's and DVD's but I can't burn them. I've tried Brasero and Gnomebaker as well as the gnome tool (I really don't know the name). The thing is that in the three applications I get a message saying that the burning process was successful, but when I re-insert the CD/DVD it is blank!! and Ubuntu keeps saying that it's a blank CD and asking if I want to burn it.

It's curious because last time I burned a CD successfully was just after 7.10 was released, (I burn the live CD for a friend) after that I hadn't tried to burn any CD, until yesterday when I realized about this. Since it has been so long since last time I burned I really can't figure what the problem could be.

---

### Post by Job Atkinson on 2007-12-21
> **philinux said:**
> I've always used k3b. It's in synaptic.

Very capable piece of software.

I've now got k3b but my music is in mp3 - what do you recommend for converting to wav.

thanks again

---

### Post by MrKlean on 2007-12-21
I had that problem alot too....Till I realized...DUH !! I was putting the disk in the wrong writer !!  LOL!!   If you have 2 like I do...make sure it's the right one !!   I never said I was smart LOL!!!

---

### Post by carloslosgrande on 2007-12-21
[FONT="Comic Sans MS"]Hi Job.
Have a look in 'add/remove applications' for wav and see what comes up. I just had a quick look and found 'sound converter'. There'll be more.
Haven't done any converting myself, haven't needed to.
You may want to set the 'show' box (top right) to 'all available apps'[/FONT]

---

### Post by philinux on 2007-12-21
> **Job Atkinson said:**
> I've now got k3b but my music is in mp3 - what do you recommend for converting to wav.

thanks again

I dont really burn audio cd's but k3b's description says it can burn one from mp3's - it must do the converting in the burn process.

> K3b is a GUI frontend to the CD recording programs cdrdao and cdrecord.
Its aim is to provide a very user friendly interface to all the tasks
that come with cd recording.

It can be used to copy CDs and burn:
 - audio CDs (from wav, mp3 or ogg vorbis files)
 - data CDs and DVDs
 - mixed-mode CDs (CD-Extra support)
 - VCDs (1.1, 2.0 and SVCD)
 - ISO files (Joliet/Rockridge and El Torito support)
 - eMovix CDs

---

### Post by The Cog on 2007-12-21
Why do you want to convert to wav? If its for burning CDs, don't bother. Launch a new audio CD project in k3b and drag the mp3s in. It'll do the right thing with them.

---

### Post by Job Atkinson on 2007-12-22
> **The Cog said:**
> Why do you want to convert to wav? If its for burning CDs, don't bother. Launch a new audio CD project in k3b and drag the mp3s in. It'll do the right thing with them.

That's just it - when I drag files in I get an error saying

[INDENT][I]**Problems while adding files to the project.**
Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.[/I][/INDENT]

I get the same message when I try to burn the wave files I made with Sound Converter.

Any ideas?

:confused:

---

### Post by TippyDad on 2007-12-22
Hello everyone,

I am somewhat Xbunto newbie.I am using Xbunto 7.10 on Pentium 800MHz PC. I am having similar issues as other Ubunto newbies. 

I am having the same problem with my CD-RW and DVD-RW drives. I had no problems reading anything on either drives, but I am unable to write anything to either drives.  I tried gnomebaker, too.  

They work well under Windows. That led me to believe that those drives have no hardware issues.

The only way I get DVD-RW drive to recognize blank CDR is that I do not change the drive. 
When I attempted to write the disc image to the DVD-RW drvie, it gets locked up. It will not let me to eject the blank media. Only way to resolve this issue is to restart the Xbunto (to unlock DVD-RW drive). I get error message every time I tried to burn anything, but it does not tell what happened. 

After switching to another drive, second drive kept reporting that the drive is empty although I kept trying different medias. 

I am not sure what to do next. 

Thank you.

---

### Post by bobpur on 2007-12-22
I've seen the "Please insert empty CD" message too. I use CDBurnerXP Pro and get this message when the program wants to use one drive and the cd to be burned is in the other drive. Put the cd in the drive the program is trying to use or switch the program to use the drive that the cd is in. My machine has a DVD/ROM with CD/RW and a DVD/RW.

---

### Post by TippyDad on 2007-12-22
Hi,

Yep. I did the same thing. Unfortunately, the default drive is DVD-RW, and I want to use CD-RW drive. The reason is that the DVD-RW locks up if it attempts to write something to CDR although it detects the blank CDR properly. I think my main issue is how to get Basero to select CD-RW drive as the default drive. It is likely to work OK. Thank you for the suggestion.

TippyDad

---

### Post by The Cog on 2007-12-23
> **Job Atkinson said:**
> That's just it - when I drag files in I get an error saying

[INDENT][I]**Problems while adding files to the project.**
Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.[/I][/INDENT]

I get the same message when I try to burn the wave files I made with Sound Converter.

Any ideas?

:confused:

Ah. Try installing the package **libk3b2-mp3**. Use Synaptic and search for k3b, or use this command in a terminal:
**sudo apt-get install libk3b2-mp3**

Then you can add mp3 files to your audio CD project no problems.

---

### Post by iamclueless on 2007-12-26
> **Darkade said:**
> I have the same problem. I can read CD's and DVD's but I can't burn them. I've tried Brasero and Gnomebaker as well as the gnome tool (I really don't know the name). The thing is that in the three applications I get a message saying that the burning process was successful, but when I re-insert the CD/DVD it is blank!! and Ubuntu keeps saying that it's a blank CD and asking if I want to burn it.

It's curious because last time I burned a CD successfully was just after 7.10 was released, (I burn the live CD for a friend) after that I hadn't tried to burn any CD, until yesterday when I realized about this. Since it has been so long since last time I burned I really can't figure what the problem could be.


Glad to hear im not alone on this one!

Ive read over so much of this forum to try and fix this and there is a simple answer that many Ubuntu users are just reluctant to admit... the program doesnt support it.  I've read people suggesting that the drive is broken, that they did something wrong, etc.  And a few will admit it is probably unsupported.  

dont get me wrong, i like the tinkering ive had to do so far.... but your average user will never be interested in a OS that will not do it all out of the box.  

The problem ive had with blank CDs is you cant mount them... and when i use Brasero, it wants to know what kind of CD ive inserted - theres no option for a  CD-RW!!!!!!!!!! wtf?

Anyway this might help you - certain brands of CD are NOT being recognized!  I've tried 4 different ones, and one of them is simply not seen at all

---

### Post by carloslosgrande on 2007-12-27
I've used Gnomebaker, Serpentine and currently use K3B - I find it simplest.
I use either Maxell or Verbatim discs.
Haven't tried any others, even though I'm in China I don't use local brands. Had some unimpressive results.

---

