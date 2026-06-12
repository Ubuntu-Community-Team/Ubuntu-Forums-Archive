---
title: "How to play MIDI files in Ubuntu?"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by user_of_gnomes on 2006-01-26
Hiya, first time poster here, I hope this is the correct section to post in. I'd consider myself an absolute beginner when it comes to Linux.  

I think Linux is absolutely amazing technology; I'm very glad I took the time to install it and explore it

However, one thing I found lacking from the beginning was the ability to play MIDI files. 

I have installed the codecs and players neccessary to play 'non-free' (I think that's what they're called) video files and music, but I still can't seem to play MIDI files with either Totem or Rhytmbox. 

I did read through the **automatix** thread, but I am not certain if I want to install an entire program just to play midi files. I'm allready short on storage space

Not quite certain as to what information anywould require but here's some general specifications:

Linux Ubuntu 32 bit (5.10? I did download a lot of updates after installing, though)
2Ghz Celeron CPU
Shuttle MV43/N
P4M266 chipset (VIA) 
AC' 97 onboard 2.1 compliant
30GB Seagate HDD
Asus ATI 9550

Any assistance would be much obliged.

---

### Post by kaamos on 2006-01-26
Instructions for hoary, also worked for me in breezy: [http://ubuntuforums.org/showthread.php?t=58859](http://ubuntuforums.org/showthread.php?t=58859)

---

### Post by cwaldbieser on 2006-01-26
[QUOTE=UbuntuRaptor]Hiya, first time poster here, I hope this is the correct section to post in. I'd consider myself an absolute beginner when it comes to Linux.  

I think Linux is absolutely amazing technology; I'm very glad I took the time to install it and explore it

However, one thing I found lacking from the beginning was the ability to play MIDI files. 

I have installed the codecs and players neccessary to play 'non-free' (I think that's what they're called) video files and music, but I still can't seem to play MIDI files with either Totem or Rhytmbox. 

I did read through the **automatix** thread, but I am not certain if I want to install an entire program just to play midi files. I'm allready short on storage space

Not quite certain as to what information anywould require but here's some general specifications:

Linux Ubuntu 32 bit (5.10? I did download a lot of updates after installing, though)
2Ghz Celeron CPU
Shuttle MV43/N
P4M266 chipset (VIA) 
AC' 97 onboard 2.1 compliant
30GB Seagate HDD
Asus ATI 9550

Any assistance would be much obliged.[/QUOTE]

timidity is a very good midi player.  It is in the repositories.  I got kmid (in kubuntu) working as well.

---

### Post by Mustard on 2006-01-26
-edit-
DOH!  This seems redundant now, as many have replied while I was typing. :)

I believe you can install timidity and freepats (freepats is listed as recommended when installing timidity).  From memory timidity works from the command line, I don't recall a gui for it.  Both are available through Synaptic Package Manager, although you might want to check out their size, since you are running out of hard drive space.

---

### Post by barisurum on 2006-01-26
I had to same problem to play midi files. So I installed automatix. Its really an amazing program. It solves many problems automatically. So I installed the MIDI package via automatix. It did all the steps about timidity or soundfonts itself.
   But I found that timidity is a software sequencer and eats up so much system performance. So I removed all of that.

   My card is a SBLive! and finally I could configure it to play midi. It may also work with audigy:

   In terminal:
   [COLOR="Red"]sudo modprobe snd_seq_midi
   sudo modprobe snd_emux_synth
   sudo modprobe snd_emu10k1_synth [COLOR="Black"](this creates the device modules for MIDI)[/COLOR]

   sudo apt-get install awesfx;asfxload
   "asfxload soundfont.sf2" for ALSA or "sfxload soundfont.sf2" for OSS[/COLOR]
    (and this is a tool to load soundfonts, you can find them on internet)

   and after that you can play midi by selecting a port "emu10k1 : 0" etc in a midi
player

    and to make these changes permanent (to load the modules at boot):
    
    [COLOR="Red"]sudo gedit /etc/modules[/COLOR]
    (Enter these lines at the end of file in editor)
    [COLOR="Red"]snd_seq_midi
    snd_emux_synth
    snd_emu10k1_synth
[/COLOR]
    save n exit. This sould work with SBLive! or Audigy (emu10k1)

---

### Post by user_of_gnomes on 2006-01-27
Thanks for all of your response;

> **kaamos]Instructions for hoary, also worked for me in breezy: [http://ubuntuforums.org/showthread.php?t=58859](http://ubuntuforums.org/showthread.php?t=58859)[/QUOTE]

I got as far as step 4 said:**
> barisurum

I've got an AC '97 onboard audio chipset, not a soundblaster. Do you think that'd work or should I go with the first suggestion? 

> cwaldbieser/Mustard

Timidity seems to be used in the tutorial Kaamos gave me, but I just can't move on because I don't understand what I'm doing wrong.

---

### Post by kaamos on 2006-01-27
Did you download the Unison.SF2.gz? The decompress command seems to wrong in the guide, so just right click on the package and choose "extract". Then continue with the instructions.

---

### Post by barisurum on 2006-01-27
No I dont think it would be helpful with AC97. Sorry didnt see that. 
  But its a known problem and if somebody searches this topic it may be helpful. 
  And I can suggest you buying a SBLive or audigy because they're perfectly supported in Linux. And you can load up to 130 Megs of soundfonts
with little system performance loss.

---

### Post by user_of_gnomes on 2006-01-27
[QUOTE=kaamos]Did you download the Unison.SF2.gz? The decompress command seems to wrong in the guide, so just right click on the package and choose "extract". Then continue with the instructions.[/QUOTE]

Yes, the unzip command did not work, however someone recommended gunzip and that does not seem to create any errors but it didn't seem to unpack it either?

I redownloaded the Unison.sf2.gz by using "wget ftp://ftp.personalcopy.net/pub/Unison.sf2.gz" 

However, I still can not do " mv Unison.SF2 Unison.sf2" even after using the gunzip command recommended by one poster. 

Is it important that I can? I do not know what that command is supposed to do. 

If I try to do this from the GUI (Gnome) I haven't got an extract option in the context menu. Also, the .sf2 file opens with Totem. That can't be good?

> barisurum

I still have a Soundblaster Live! 5.1 with EMU-101K chip lying around. If I do as you say, will that allow me to play MIDI files in Totem?

---

### Post by kaamos on 2006-01-27
The point is just that you should end up with a file called "Unison.sf2" (case sensitive). So if you have a .sf2 file, then you have succesfully extracted the package. Then just continue from
> sudo mv Unison.sf2 /etc/sounds/
...

---

### Post by barisurum on 2006-01-27
I dont know if totem plays midi or not, maybe you can make it play with a plugin to gstreamer. I use Kmid. its an excellent player.
And if you have an emu10k1 then it must work for you too. (It did for me)

---

### Post by PatrickMay16 on 2006-01-27
> I still have a Soundblaster Live! 5.1 with EMU-101K chip lying around. If I do as you say, will that allow me to play MIDI files in Totem?
You won't be able to play midi files in Totem or another player like that, I'm afraid. You might, but I've looked around and I haven't found any plugins that allow it.

But using the Sooundblaster Live! would be much nicer for MIDI, since it will do all the stuff in hardware rather than software, so the CPU doesn't have to do much with it. Therefore you can use the computer for other stuff without causing the midi file which is playing to pause a bit or have clicks or pops and other choppy noise appear in it; that's a problem I had with timidity.

If you decide to get your soundblaster live working, use these threads: 
[http://ubuntuforums.org/showthread.php?t=58859](http://ubuntuforums.org/showthread.php?t=58859)
[http://ubuntuforums.org/showthread.php?t=8736&highlight=midi+hardware+synthesis](http://ubuntuforums.org/showthread.php?t=8736&highlight=midi+hardware+synthesis)
And if you want some soundfonts, you could email me if you like. My address is [email]dusthillresident@gmail.com[/email]

If you need a midi file to test that things are working, here's one (I composed it myself):
[http://dusthillguy.netfirms.com/GrantKelly.mid](http://dusthillguy.netfirms.com/GrantKelly.mid)
Good luck.

---

### Post by user_of_gnomes on 2006-01-27
[QUOTE=kaamos]The point is just that you should end up with a file called "Unison.sf2" (case sensitive). So if you have a .sf2 file, then you have succesfully extracted the package. Then just continue from[/QUOTE]

Well, I did exactly as the rest of the guide said but I still can not play MIDI files, though - I can use the command pmidi without errors and point it to a midi file, but once that is done, nothing happens. I can only abort using ctrl + c. 

> PatrickMay16

I'd play the midi file, but I can't. I'll look into installing the soundblaster and getting that to work. I think this is all far too difficult if you ask me. 

> barisurum

I looked for kmid with the synaptic packet manager; it seems to be for KDE. I seem to have Gnome installed. Does it matter? Should I install it?

---

### Post by barisurum on 2006-01-27
> I looked for kmid with the synaptic packet manager; it seems to be for KDE. I       seem to have Gnome installed. Does it matter? Should I install it?

   I thought about that twice too... But I study music at conservatory. Music software and midi players are important for my education.
   If you install Kmid, synaptic will install KDE's base libraries. It will take aprox. 60 Megs of space. If you can find a fine app. for Gnome dont do it. I did it because I need Rosegarden 4 to study music, and its a KDE app. I searched for a fine gnome GUI app. to play midi, but I think Kmid is the best.

---

### Post by user_of_gnomes on 2006-01-27
[QUOTE=barisurum]I thought about that twice too... But I study music at conservatory. Music software and midi players are important for my education.
   If you install Kmid, synaptic will install KDE's base libraries. It will take aprox. 60 Megs of space. If you can find a fine app. for Gnome dont do it. I did it because I need Rosegarden 4 to study music, and its a KDE app. I searched for a fine gnome GUI app. to play midi, but I think Kmid is the best.[/QUOTE]

I seem to be able to access Kmid from GNOME after having installed all the files required, however, when I load a MIDI file it does play, but I hear no music.

---

### Post by barisurum on 2006-01-27
If you installed the SBLive!

   1. Did you do the steps I first wrote in [COLOR="Red"]red color[/COLOR] in my first reply?
  
   2. If you did them then did you load a soundfont? Like

   cd /home/YOURHOME/YOURSOUNDFONTDIR/
   asfxload realfont.sf2 (or another one) or
   (for OSS)sfxload Unison.sf2

---

### Post by PatrickMay16 on 2006-01-27
[QUOTE=UbuntuRaptor]Well, I did exactly as the rest of the guide said but I still can not play MIDI files, though - I can use the command pmidi without errors and point it to a midi file, but once that is done, nothing happens. I can only abort using ctrl + c. 
[/QUOTE]

Hmm... What midi file are you testing it with? Also, could you run the command
> 
pmidi -l

and copy+paste the output it gives? That might help us find out the problem.

---

### Post by user_of_gnomes on 2006-01-27
> **PatrickMay16]Hmm... What midi file are you testing it with? Also, could you run the command

and copy+paste the output it gives? That might help us find out the problem.[/QUOTE]

I have tested it with two midi files that previously worked on Windows XP. They are stored and copied to this PC from an external HDD. If it is of any importance said:**
> If you installed the SBLive!

I can not answer your question yet, I will install the SB live! sound card tomorrow and do as you suggested even if I can get it to work before that. Always room to grow.

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=PatrickMay16]You won't be able to play midi files in Totem or another player like that, I'm afraid. You might, but I've looked around and I haven't found any plugins that allow it.[/QUOTE]
timidity will let you convert midi files to .ogg or wave files that can be played through totem, amarok, xmms, etc. though.

---

### Post by user_of_gnomes on 2006-01-28
[QUOTE=barisurum]If you installed the SBLive!

   1. Did you do the steps I first wrote in [COLOR="Red"]red color[/COLOR] in my first reply?
  
   2. If you did them then did you load a soundfont? Like

   cd /home/YOURHOME/YOURSOUNDFONTDIR/
   asfxload realfont.sf2 (or another one) or
   (for OSS)sfxload Unison.sf2[/QUOTE]

Hello, Barisurum.

Thanks for your excellent information. I installed the SB! Live 5.1 soundcard and then proceeded to do as you said. 

Thanks to everyone else for their advise as well. 

> timidity will let you convert midi files to .ogg or wave files that can be played through totem, amarok, xmms, etc. though.

If I could use Kmid as the default MIDI player, I would not have to convert them. Do you know how I can make it so that when I click on a MIDI file it automatically opens (and plays) in Kmid?

---

### Post by barisurum on 2006-01-29
> If I could use Kmid as the default MIDI player, I would not have to convert them. Do you know how I can make it so that when I click on a MIDI file it automatically opens (and plays) in Kmid?  

    Right click a midi file > Properties > Open with

For some free and good soundfonts:    
[COLOR="MediumTurquoise"]
[http://hammersound.net/cgi-bin/soundlink.pl](http://hammersound.net/cgi-bin/soundlink.pl)[/COLOR]

                                     \\:D/ \\:D/ \\:D/ \\:D/ 
                                            :-D :-D :-D 
                                                  :mrgreen:

---

### Post by user_of_gnomes on 2006-01-29
[QUOTE=barisurum]Right click the file > Properties > Open with

For some free and good soundfonts:    
[COLOR="MediumTurquoise"]
[http://hammersound.net/cgi-bin/soundlink.pl](http://hammersound.net/cgi-bin/soundlink.pl)[/COLOR][/QUOTE]

That's what I'm currently doing, but that's still two clicks too much if you ask me. ;) Is there a way to have Kmid open when left clicking on a MIDI file? 

Thanks for the soundfonts, I added the webpage to my favourites bookmarks. Although they only seem to cover certain instruments and not the entire spectrum; am I going to have to load several soundfonts simulteanously when I download them from that website? 

So far I've got three types of soundfonts but I'm looking for some original Windows soundfonts if those are even available for download.  Any idea where to get some?

---

### Post by barisurum on 2006-01-29
Hello Raptor

  > Is there a way to have Kmid open when left clicking on a MIDI file?

   If you did this configure thing. Left click a midi file. It must have been available for every midi file.

   In the page of hammersound there is this [COLOR="Red"][COLOR="Yellow"][COLOR="DarkRed"]"collections"[/COLOR][/COLOR][/COLOR] part 
 
   Explore a little bit :)

---

### Post by user_of_gnomes on 2006-01-30
[QUOTE=barisurum]Hello Raptor

  

   If you did this configure thing. Left click a midi file. It must have been available for every midi file.

   In the page of hammersound there is this [COLOR="Red"][COLOR="Yellow"][COLOR="DarkRed"]"collections"[/COLOR][/COLOR][/COLOR] part 
 
   Explore a little bit :)[/QUOTE]

Heya, Barisurum. 

You are right, I should explore more. Thanks for helping me on my way!

---

### Post by fmonjaraz on 2008-04-21
How would I play a kar/midi file in hardy????

---

