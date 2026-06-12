---
title: "Grip will rip and encode but the mp3 files won't play"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-12-01
Hello, I recently installed Grip and Lame, and after setting my configuration exactly as it was on the Grip users guide: [http://nostatic.org/grip/doc/ar01s04.html#mp3config](http://nostatic.org/grip/doc/ar01s04.html#mp3config)

and configuring it with Lames wiki page: [http://wiki.hydrogenaudio.org/index.php?title=LAME#High_quality:_HiFi.2C_home_or_quiet_listening](http://wiki.hydrogenaudio.org/index.php?title=LAME#High_quality:_HiFi.2C_home_or_quiet_listening)

this is what I choose: -V2 --vbr-new %b %w %m

I kept the default settings for everything and only changed what was different on the user guide. I also kept the Generic SCSI Device blank, and the (1)wav filter and the (2)disk filter commands blank.

The result was that the disk ripped to newmp3 and then mp3, made a m3U playlist, and the mp3 file with music files inside, but when I try to play the files using Beep Media Player, they don't play at all. They list with the name, but it won't play.

When I rip my CD's to 192 kbps on windows xp, and open the file in Beep Media Player the files play perfectly.

Do I need to configure something differently for the Grip encoded mp3 files to play?

Thanks,
-c.

---

### Post by lloyd_b on 2006-12-01
I'm not familiar with Beep, but could it be that it simply doesn't understand VBR (Variable Bit Rate) encoded files?

To test this, replace the "-V2 --vbr-new" with "-b 192" to tell Lame to encode to 192kbps CBR (Constant Bit Rate), and see if Beep likes this any better.

Lloyd B.

---

### Post by crimesaucer on 2006-12-01
I'll give it a try.

***Nope, it didn't work with "-b 192"

---

### Post by crimesaucer on 2006-12-01
Ok, this detail might help somebody fix my problem that knows Grip.

When I was comparing file permissions of my working mp3 files ripped in Windows Xp mp10, they had the size measured out correctly for each song like 4.5 MB or 9.6 MB. 

But with my Grip ripped mp3 files they all said 128 Bytes. Which means they are empty, huh? Thats the size of the info and icon but no music, so what happened to the mp3 music?

---

### Post by crimesaucer on 2006-12-01
So, if nobody knows how to fix this, is there another quality CD ripper for xubuntu that will rip with cdparanoia and encode with lame.

---

### Post by dwblas on 2006-12-01
After screwing around with ripping for a while on XUbuntu, I finally installed KAudioCreator and AmaroK because they are great apps and "just work".  I don't like or need the KDE bloat but KDE does have some excellent apps.

---

### Post by crimesaucer on 2006-12-01
Yeh, I'm loving my xubuntu edgy right now so I wouldn't want to switch desktops, I have beryl installed and configured perfectly with xfce4, and am happy with everything else I have on xubuntu. I just got rid of grip, and am trying a few different ripper encoders, and if they fail, I can always use my dual boot Windows Xp's MP10 since it's just collecting dust...

---

### Post by dwblas on 2006-12-01
Just install KAudioCreator and Amarok on Xfce.  You don't have to use KDE.  There are some other dependencies installed but that is true with any GUI.

---

### Post by crimesaucer on 2006-12-02
Thanks, I'll try it out, I just thought it was for the KDE desktop only. 

These are what I've tried so far:
Grip -- after reading many forums and the user guide, I was still only getting the 128kb file after rip/encoding using lame. I didn't try the ogg though.

ripperx -- I wasn't sure of the settings and couldn't find any user guides or forum tutorials.

goobox -- wasn't sure of the settings and couldn't get it to work. I also couldn't find any guides or explanations of how many kbsp "mp3 quality #5" is?

Sound Juicer -- works, but only has ogg, wav, or flac available. I ripped a Nirvana song on both Windows Xp (192kbsp) and on Sound Juicer ogg CD quality. The ogg file was smaller, and even though there was a slight difference in sound, I couldn't tell which I liked better, ogg seemed to pay more attention to the base sound. I'm going to re-rip my CD collection in ogg format one of these days when I read up a little bit more on the proper settings and configuration.

I also searched through Synaptic and tried a few packages but was unable to use them because I found no guides anywhere explaining on how to use these command based rippers.

What I really want is something that will have the cdparanoia because I want to rip some of my scratched CD's that aren't rippable on MP10.

---

### Post by dwblas on 2006-12-03
> I want to rip some of my scratched CD'sGood idea.  One program that I didn't try was Jack.  I think it is based on cdparanoia.  If Jack works better, let me know.

---

### Post by logos34 on 2006-12-04
[QUOTE=crimesaucer;1830174]

this is what I choose: -V2 --vbr-new %b %w %m

take out the '%b' (you've already specified vbr) so that it reads:

'-V2 --vbr-new %w %m'

That works for me.

---

### Post by logos34 on 2006-12-04
or try:

-V 2 --vbr-new --add-id3v2 --pad-id3v2 --ta "%a" --tt "%n" --tl "%d" --ty "%y" --tn "%t" %w %m

---

### Post by crimesaucer on 2006-12-05
Thanks, do you know the ogg settings for similar (192kbsp) sound?

---

### Post by logos34 on 2006-12-05
ogg quality 6 = 192kbps vbr.

Here's my command line:

-q6 %m -a %a -l %d -t %n -d %y -G %g -b %b %w

see if that works for you.

---

### Post by crimesaucer on 2006-12-05
I think I'll reinstall grip and try it again with the the ogg settings. Thank you.

---

### Post by logos34 on 2006-12-05
that command-line is just the default with '-q6' in place if the '-o'.

Rip a test track in ogg.  It should playback fine in amarok, but if you have a problem in xmms or audacious, try ripping it again with the id3 boxes unchecked (grip>config>Id3>uncheck all the 'Add id3 tags..' boxes).

---

### Post by crimesaucer on 2006-12-07
I tried it again and I still got the same result after ripping a song that I did earlier. No Song, and just a 128kb file of the songs name and track order.

I don't understand it. I think I must have the settings incorrect, but I thought it was the same as the user guide and forums?

I guess I'll just use sound juicer.

---

### Post by logos34 on 2006-12-08
That 128kb routine sounds vaguely familiar, but I can't recall now where I ran into it.

Check your Encoder executable line again.  Should be '/usr/bin/oggenc' or '/usr/local/bin/oggenc' (or the path to where you moved it if applicable).  If it just reads, say, '/usr/bin' and you have one of the 'Add id3 tag' boxes checked Grip will rip the track but not encode it, outputting a tagged but empty .ogg file (though mine were 2.1kb) and (if enabled) an .m3u playlist.  

Don't know what else to suggest.

---

### Post by quarkhirad on 2006-12-08
To play mp3 files try playing them using XMMs. U can install it by synaptic pakage manager. 

Cheers

---

### Post by crimesaucer on 2006-12-09
Hey logos34, That sounded a lot like my problem. I did have my executable configured as /usr/bin/lame and /usr/bin/oggenc so I tried it again with out the id3 tags checked. I think I misread it last time and only unchecked the bottom two of them and kept the top one checked.

When I unchecked them all, the song ripped to newmp3s perfectly. Then I compared sound quality of the WMP 192kbps and the Grip ogg q6 (which turned out to be a variable 170-192kbps) and the ogg sounded really good. The harmonics were much better and the sound was like I was in the room of the musicians.

Thank you. I'm going to rip my whole collection in ogg, and now I'll have even less use for my Windows Xp partition.

Thanks again.

---

### Post by logos34 on 2006-12-09
My only afterthought was that for some reason oggenc didn't get installed.

Yeah, the general consensus seems to be that ogg offers the best quality-to-size ratio -- it would be my format of choice but for the lack of support among portable media players.  q6 is roughly equal to 192k (the 'nominal' bitrate), but its vbr so you end up with an average rate that's usually less.    

Glad to see you got Grip working (I sympathize -- took me a while too to get it configured correctly with lame and all).  It's the best replacement i can come up with in Linux for Exact Audio Copy and Cdex in windows.  Lots of people use sound juicer because it's faster, but I just don't trust one-pass ripper-encoders where you can't configure the ripper (which is why I use iTunes only as a jukebox).  My attitude is: Do you want it ripped fast or do you want it ripped right? 

Ciao

---

### Post by crimesaucer on 2006-12-10
No doubt, sound quality is far more important than fastness and easiness. 

I still have one weird problem though, I am able to rip the songs to a folder, and have added the %t to the %n so it looks like this in the rip file format: ~/newmp3/%A/%d/%t %n.wav

So the songs now have the number in the title and are in order in my file and music player, but when I tried to sync my device (iRiver T30 with ums firmware to work with linux), the songs transfer out of order and some get skipped, do you have any idea what that might be?

I don't know if it's because I just used drag-and-drop from a thunar(xubuntu) folder to a thunar(xubuntu) usb device music folder, but when I did the same drag-and-drop method with a ogg folder from Sound Juicer it transfered perfectly. But, to be fair, I also transfered some mp3 192kbps music folders that were ripped in WMP10, and they were all in order except for song #7 that was the first song in each of the music folders. They were all in this order #7,#1,#2,#3,#4,#5,#6,#8,#9...and so on.

The Grip were in like #8,#2,#5,#6,#10,#12 and only song #2 would play on my device and then it would fast forward to the next album.

I'm going to redo my firmware, try it again, and then try installing iRivers jukebox with wine to see if that syncs and transfers properly.

Thanks for you help with grip.

---

### Post by logos34 on 2006-12-10
no idea on that one.

---

### Post by crimesaucer on 2006-12-10
I tried it over and over again and still couldn't get it to work correctly. Even trying to delete the music folder in the usb/device/music folder wouldn't erase the folder from my iRiver device, even when it was deleted and sent to the trash.

Then I decided to see if it wasn't the grip file, and was just the iRiver T30 not syncing correctly since it's supposed to only be able to use the iRiver Plus 2 or WMP10/11. 

So I installed the iRiver jukebox onto my Windows Xp after I had transfered my Grip "ripped" ogg music file to my Windows E: drive partition. 

From there I successfully deleted the messed up ogg file from my device, and then uploaded the same exact Grip "ripped" ogg file that had been syncing wrong when using the usb ums device transfer in xubuntu.

When in Windows using the iRiver plus 2, that ogg file loaded perfectly in order and sounded the best my iRiver has ever sounded. I've been trying to get wine to work with the same iRiver Plus 2 music jukebox on xubuntu but that is another thread.

Thanks again for the help, and all of the effort was worth it because the sound of the ogg is far better then .wav and .mp3 at the same 192kbps bit rates.

Latter.

---

