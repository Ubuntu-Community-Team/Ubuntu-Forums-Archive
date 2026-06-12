---
title: "Natural Reader / Other Text-to-Speech or Screen Readers"
date: 2008-05-11
forum: Assistive Technology &amp; Accessibility
---

### Post by variableenigma on 2008-05-11
I'm looking for a text-to-spech program that I can run in Ubuntu.

I would like to install and use Natural Reader in Ubuntu using Wine. It is the most natural-sounding text reader I can find, and that is very important to me.

I tried installing the trial version already. It did install and I got it running, but I encountered a problem with the audio. I think the problem is that it doesn't recognize my drivers. I'm not sure that's fixable, but if it is, let me know.

The paid program also has a text-to-mp3 feature, which I think I would be able to use on Ubuntu, because the program only has to convert the file, and then I can play it on any Ubuntu-friendly mp3 player.

Has anyone tried this?

Does anyone know of a NATURAL-SOUNDING text-to-speech reader that works well in Ubuntu?

(I cross-posted this thread to Wine)
Thanks in advance!

---

### Post by omelette on 2009-02-01
Old post I know, but for the record, it is possible to get NaturalReader working with Wine.  I managed to get NR 6.6 working with Wine 1.1.9 (somehow!) and it worked fine until I upgraded to Wine 1.1.14, which killed it!  I have just spent 8 hours trying to revive it, to no avail.  In desperation, I even made the big mistake of uninstalling Wine to try earlier versions, even deleting all the other Windows s/w I had installed, but nothing worked - NR either doesn't run or complains that no voices were found!  Utterly fustrating...

Regarding other good-sounding text-to-speech software, I looked everywhere, tried everything and NR was easily the best.  The program itself is really sub-standard imo, real shoddy programming, though the latest version (7.1) seems a bit more functional, but likes M$ .NET installed (Winetricks makes this pretty painless) - 'no voices found' with this as well, but it works fine with WindowsXP...

---

### Post by notlistening on 2009-02-03
Ah reposting has bore new fruit. The answer to your problem is that they changed the default installation environment from windows2k to windows XP which in turn broke the SAPI install (ms text to speech engine installer.) So to get it to install in wine open up the configuration panel and change the default run environment to windows 2k. This will solve the no voices error your experiencing. I can provide a link to the installer from Microsoft. 

Not sure if you have sight and not sure how accessible with ORCA the configuration of wine is, but if you are struggling with this then I have some neat tricks for a commandline install from the project I am currently working on. This allows you to use MS compatible voices in Linux apps like ORCA. As a bi-product of this apps such as textaloud work nicely which I recommend for tts. If your not too fussy on features the free software in the development SDK will produce you a .wav file that can be converted to mp3.  



Tom

---

### Post by omelette on 2009-02-03
Tom, you're a life-saver - this is one of my "absolutely essential, can't live without apps" and I had spent another fruitless day yesterday trying everything possible to breathe life back into it, alas in vain!  Not what you suggested obviously 'cos it again has a heartbeat, or at least a voice! :D

Things aren't perfect though - when I try to convert to mp3/wav, I get an error message saying there's something wrong with the voice, which must first be repaired! I am working with the latest NR version and on its own it still gives me the "no voices found" message, but thankfully it finds 'Mike' when I install this voice-file!  In other words, there is no 'Microsoft Sam' present by default - is this the MS link you are referring to?  I installed SAPI4SDK but it didn't make any difference.  I googled SAPI5.1 which is over 130megs which seems over-kill, especially considering I had 'MS Sam' by default with Natural Reader 6.5...

Apart from testing and rejecting ORCA (too used to 'Mike'), I have little knowledge of its workings.  The only other thing I have played with is Speex, which is pretty impressive.  If only I could get my old mp3 player to play these files...

---

### Post by omelette on 2009-02-03
Quick update - sorted the missing MS voice(s) in Natural Reader 7.1 by simply first installing NR 6.5 followed by 7.1, then the voices are available.  The mp3 creator problem appears to be a bug/incompatibility with Wine, or as a result of the 'default OS as Win2k' fix, for although 7.1 will not work at all at mp3/wav/ogg creation, 6.5 will create both wav and ogg files, but not mp3, even though it worked fine prior to these 'issues'.  So I guess it's back to 6.5, and as long as I can continue creating ebooks audio files, even if it involves a work-around, I can live with it - still better than having to work with M$! :)

---

### Post by raygj on 2009-03-04
Has anyone tried this?
Im using a very good scottish voice in festival (very natural & easy to understand and best all it doesnt "grate on you nerves" after listening to it for a while ) I'm  useing the enhanced Nitech HTS scottish voice (nitech_us_awb_arctic_hts)
goto <http://ubuntuforums.org/showthread.php?t=751169>
[ (HOWTO: Make festival TTS use better voices (MBROLA / CMU / HTS))]("http://ubuntuforums.org/showthread.php?t=751169")
1 follow the "introduction" section
```
sudo apt-get install festival festlex-cmu festlex-poslex festlex-oald libestools1.2 unzip 
```
2 do the "Installing the standard Festvox diphone voices" but only install the standard voice "festvox-don"
```
sudo apt-get install festvox-don 
```
3 jump to the "Installing the enhanced Nitech HTS voices" but only install the "scottish voice"
```
 mkdir hts_tmp 
cd hts_tmp/
wget -c http://hts.sp.nitech.ac.jp/archives/2.1/festvox_nitech_us_awb_arctic_hts-2.1.tar.bz2 
```

4 continue on with  "Unpacking the voices"
```
for t in `ls` ; do tar xvf $t ; done
```

5 continue on with  "installing the voices"
  ```
sudo mkdir -p /usr/share/festival/voices/us
sudo mv lib/voices/us/* /usr/share/festival/voices/us/
sudo mv lib/hts.scm /usr/share/festival/hts.scm
```

6 continue on with  "Tidy up"
```
cd ../
rm -rf hts_tmp/
```

7 continue on with  "Testing voices and choosing a default voice" section and stop when you get to "Installing Festival 1.96 from source"
heading.

8 open a pdf file with "okular"pdf viewer

9 select "Tools/T Speak Current Page" sub-menu

10  wait for it to start speaking (there is a delay the first time you select "Tools/T Speak Current Page" as it has to start up "festival"
11 enjoy!


 if you want, you can   use KTTS - the KDE Text-to-Speech system
 ```
kttsmgr 
```
right mouse click on its icon,
select "configure"submenu,
select "Talkers"tab,
click on "ADD" icon,
set "Language" to "English (United Kingdom)",
set Synthesizer to "Festival Interactive",
click "ok" button,
click on " Festival Interactive nitech_us_awb_arctic_hts",
click "up" button,
 click "apply" button,
click "ok" button

- the KDE Text-to-Speech system - is a plugin based service that allows any KDE (or non-KDE) application to speak using the DCOP interface.

---

### Post by go_beep_yourself on 2010-03-18
> **raygj said:**
> Has anyone tried this?
Im using a very good scottish voice in festival (very natural & easy to understand and best all it doesnt "grate on you nerves" after listening to it for a while ) I'm  useing the enhanced Nitech HTS scottish voice 

Do you know if the enhanced Nitech HTC voices work with espeak as well? I know mbrola voices work with both espeak and festival.

---

### Post by pauljay123 on 2010-03-30
Pretty sure Nitech HTC doesn't work I tried it

---

### Post by erwinsoo on 2010-06-12
Cepstral voices for Linux. Uses Swift engine but no GUI. 

Gespeaker 0.7 for ubuntu incorporates Mbrola voices

---

### Post by go_beep_yourself on 2010-06-21
I just wrote a guide on my blog having to do with text to speech. Here it is.

[http://linuxinnovations.blogspot.com/2010/06/have-your-ims-spoke-to-you-with-good.html](http://linuxinnovations.blogspot.com/2010/06/have-your-ims-spoke-to-you-with-good.html)

---

### Post by Marinity on 2010-09-22
I followed your guide,but can't fix it

---

### Post by go_beep_yourself on 2012-05-11
> **Marinity said:**
> I followed your guide,but can't fix it

What do you mean exactly? Could you give some more specific details? Full instructions are on the front page here at Github.

[https://github.com/BullShark/JSpeak](https://github.com/BullShark/JSpeak)

---

### Post by overdrank on 2012-05-11
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

