---
title: "Shuffle iPod on Ubuntu 6.10 connection help"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-03-06
Hello

I've looked around and found various advice on how to connect up an ipod. I think the shuffle version (the postage stamp sized one) is different however because I still can't get it to work. I have probably deleted most things on the ipod by now. 

I can get Rhythmbox to see the ipod. I have tried just dragging files onto it but without success. I have used Sound Juicer to extract music from a cd. I have .ogg files apparently. I have tried gtkpod but it says it dosn't recognise the .ogg files.

How do I get music files onto the shuffle? 
What format are the files that run on a shuffle?
What is the directory structure on the shuffle and should there be OS files on it (msdos and iosys)?
How do I create the iTunesDB?
Do I have to create a mirrored file structure on my hard drive and then synchronise the shuffle with it?

Any help would be gratefully appreciated.

Regards
Bob

---

### Post by ichigo on 2007-03-06
Hi!

I have a nano not a shuffle, but I assume that there's not much difference. 
I think the reason why you can't copy the files to your iPod is that you've created *.ogg files. Your iPod can't play them. I suppose that's why gtkpod won't copy them. Have you tried to copy mp3 files? You could try to convert some .ogg files to .mp3 using SoundConverter etc.
Or you could rip your cds directly to mp3 (I use grip for that).
The fact that iPods don't read ogg files was actually the reason why I have converted all my music to mp3...

On your iPod you should see some folders, but I suggest you don't touch them. Normally gtkpod, Rythmbox, Amarok etc. take care of changing the iTunesDB.

Regards
Pascal

---

### Post by bwallum on 2007-03-07
Got it going again by repairing Windows and running iTunes. What a pain. I will now try and get it running with Ubuntu now that I know it is functioning ok in itself. I have only been using Ubuntu since the weekend so apologies if I'm not up on all the techy speak. However I've seen enough to be serious about using Ubuntu for production. This past week or so  MS has had my hard drive chattering away on updates. They must have screwed up somewhere. Looks like a dodgy earlier upgrade has messed up more than it fixed. Everybody I know has been reporting strange sluggish behaviour. Is MS the ultimate virus? I ask myself.

Back to topic, I have downloaded Grip (isn't it easy to add and remove applications!) and it is currently trying to rip a CD. VERRRRYYY SLLLLOOOWWWLLLLYYYY. Any suggestions?

Rgds, Bob

---

### Post by ichigo on 2007-03-10
> **bwallum said:**
> Back to topic, I have downloaded Grip (isn't it easy to add and remove applications!) and it is currently trying to rip a CD. VERRRRYYY SLLLLOOOWWWLLLLYYYY. Any suggestions?
There are two probable reasons that came to my mind: 
[LIST]
[*]DMA: Check if DMA is switched on for your CDrom drive. you can check this with ```
hdparm /dev/cdrom
``` If it is not switched on, see one of the many posts of how to switch it on.

[*]CDParanoia: Grip uses CDPrarnoia, which - as far as I know - tries to correct errors of dirty or damaged CDs. Grip should be faster if you disable CD Paranoia in "Configuration->Rip->Ripper"
[/LIST]

Pascal

---

### Post by bwallum on 2007-03-10
dma switched on, tried GRIP, it works now! No idea why but possibly something to do with Sound Juicer running at the same time?? Sound Juicer kicks in by default when a CD is inserted. How do I stop that happening?

Good news is Grip really flies when working!

Thanks for your help

Regards, Bob

---

### Post by ichigo on 2007-03-11
Um, I've got German menus, so I don't know the exact English translation. Just look for something similar :)
Go to System -> Configuration/Preferences -> removable media
click on the second tab and you will find the Preferences for Audio-CDs.
Uncheck the box if you just want to disable soundjuicer. If you want grip to pop up when an Audio-CD isinserted, substitute soundjuicer with grip.
Regards, Pascal

---

### Post by bwallum on 2007-03-11
Hole in one Pascal! Thank you very much. That has helped me a great deal. I am not too sure what an executable looks like in Ubuntu, I'm used to the MS .exe stuff (seems like the dark ages now, just thinking about it!). What is the file I need to open to get Grip to run? That is, what do I put in the text box for Audio-CDs preferences?

Thanks again, another rung up the learning curve!

Rgds, Bob

---

### Post by ichigo on 2007-03-11
Most programs in Linux are linked when you install them. This means that you just have to type their name. (I usually find out the correct name by guessing.)
To run a program from command-line, you just have to type its name and - if you need them - program options. You can find out about the possible options by running [program name] --help (where [program name] is any program), e.g.
```
grip --help
```
When you insert an Audio-CD, Ubuntu will execute the syntax of the text box in some invisible terminal, i.e. you have to use command-line syntax. 
I suppose that you want grip to open and to look at the CD you have just inserted. With the above code you may find out that "--device=DEVICE" will make grip look at the DEVICE. Using the placeholder for the corresponding disc drive "%d", you write into the text box:
```
grip --device=%d
```

Pascal

---

### Post by bwallum on 2007-03-11
Wow.. just like that! It worked, I just put 'grip' into the 'play audio cd disks when inserted' edit box and...it did just that!

Thanks Pascal, really good succinct help, I appreciate it.

Regards, Bob

---

### Post by ichigo on 2007-03-11
Well, there's a difference between "grip" and "grip --device=%d" if you have more than one cdrom drive. With "grip", grip will just be opened when you insert a CD. But if you put the CD in the "non-standard" drive (the "standard" drive being the one specified in Grip->Configuration->CD) grip will be opened but won't see the inserted CD....
But if you have only one drive, "grip" will do :)
Nice that I could help you!
Pascal

---

### Post by Azakus on 2007-03-11
Install Soundconverter and it will be able to convert .ogg files to .mp3 files. Just change the preferences to MP3 output.

---

### Post by ichigo on 2007-03-11
> **Azakus said:**
> Install Soundconverter and it will be able to convert .ogg files to .mp3 files. Just change the preferences to MP3 output.

I haven't recommended soundconverter since it messes up the with the track length. And it seems I'm not the only person... [http://ubuntuforums.org/showthread.php?t=368046](http://ubuntuforums.org/showthread.php?t=368046)
Haven't tried gnormalize though :)

---

### Post by bwallum on 2007-03-11
grip --device=%d it is...sorry I missed the obvious there!

---

### Post by bwallum on 2007-03-11
I'll hold back on the Soundconverter...Perhaps you could help me a tad more with this. Grip comes up fine and I see the files. I am thinking that I would like them in an iPod readable format. Would MP3 do that?

Then when I know the iPod readable format how do I rip with Grip? Do I use encode and rip? I have found the '~/mp3/%A/%d/%n.wav' command(??) in the grip>config>rip>ripper: rip file format box. I don't know what this means. 

If I try the rip and encode option I currently get this error:Invalid encoder executable

---

### Post by ichigo on 2007-03-11
Yes, mp3 is iPod readable.
To encode into mp3 you will need to install lame (That's the case for any mp3 encoding program). I'm not sure if you need lame or gstreamer-lame; they are both in the multiverse repos and can be installed via synaptic.
See [http://www.ubuntuforums.org/showthread.php?t=107385](http://www.ubuntuforums.org/showthread.php?t=107385) for more details.

'~/mp3/%A/%d/%n.wav'  is just the format of the wav-filenames Grip can create. The line says that the files will be saved like [Your home directory]/mp3/Artist/Album name/Songtitle.wav.
In config->encode you will find that you can choose between some decoders. After installing lame you should find it there. Choose it.
Then you should already be create mp3s with "Rip + Encode"... 

 If you want another bitrate, you have to modify the command-line box.

---

### Post by bwallum on 2007-03-11
I am now listening to Bach on my shuttle ipod. Thank you very much indeed. Still lots to learn, not 100% sure what I've done but I could not have done it without your guidance. Thank you very much.

I put lame in the search box of Synaptic Package Manager then loaded it, then:
Grip-Config>Encode>Encoder: Encoder choose lame
Then I used Grip to rip (lost the file! Then found it with a search)
Then fired up gtkpod, plugged in Shuttle iPod to USB port
Then copied playlist made from ripped files to Shuttle (not too sure how to be honest)
Then .... listened....Goldberg Variations...joy, a man worth his life!

Many thanks again!
Bob

---

