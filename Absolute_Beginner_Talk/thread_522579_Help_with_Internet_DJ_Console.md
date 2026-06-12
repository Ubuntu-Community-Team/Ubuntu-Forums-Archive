---
title: "Help with Internet DJ Console"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-08-10
Well, I installed the program 'Internet DJ Console'.  I made my playlist, and setup the server info, but I need to be broadcasting to two different stations at once.  Is there anyway to do this in IDJC?

Thanks.

---

### Post by Yes on 2007-08-10
Bump.

---

### Post by Yes on 2007-08-11
Bump.

---

### Post by Yes on 2007-08-11
Bump.

---

### Post by Yes on 2007-08-12
Bump.

---

### Post by Steveway on 2007-08-12
Don't Bumb that often!
You need the new version 0.7.0
> Changes in version 0.7.0

Implementated a new, more powerful streaming architecture with multiple streams possible, greater control over quality settings, ability to change the bitrate live on air, and the ability to stream from a prerecorded file with the metadata preserved.

Removed the MP3=utf8 option. This option is now always turned on meaning that mp3 metadata is always encoded as utf-8.

In the mixer altered the way microphone signals are processed when the microphone buttons are muted. This greatly reduces the amount of CPU used since half of all CPU usage by the mixer was going into processing the microphone signal.

New license: GNU General Public License version *3*.



Next time don't bumb that often.

---

### Post by Yes on 2007-08-12
Sorry, I didn't think that bumping every 16 hours was too often.

Here's a quote from he IDJC webpage about version 0.7.0:

> **At present this version is pre-alpha on account of missing functionality in the new streaming module. Only download this if you are curious about what the next version is going to look like. Package maintainers should avoid all the 0.7.0 pre-releases since they contain nothing extra that is usable at present.**

So does that mean that it isn't possible to stream to two stations with my current version (0.6.9)?

Thanks.

---

### Post by Steveway on 2007-08-13
Yes and it seems that 0.7.0 has just gotten the stable status, according to the sourceforge site.

---

### Post by Yes on 2007-08-13
Ok, I downloaded it and am following the instructions on [this](http://www.onlymeok.nildram.co.uk/download.html) page for installation.  I tried running the command './configure', but it says that I need to install jack version .98 or higher...and I jack version 3.11.  Do you know what the problem might be?

Thanks.

---

### Post by Steveway on 2007-08-13
$sudo apt-get build-dep idjc
That should install all necessary files for compiling it.

---

### Post by Yes on 2007-08-13
It worked perfectly!  Thank you so much!!!

Edit:  Is it possible to set the bit rate lower then 45?

---

### Post by Steveway on 2007-08-13
No Problem. Don't forget, the terminal is your friend and please edit the Thread-title and add an [Solved] to it.

---

### Post by Yes on 2007-08-14
Concerning my question in my last post, I've read somewhere that ogg is a music filetype, like mp3.  Does that still mean that when changing the bitrate in the ogg frame, I'm changing it for mp3s?  Because I don't see a frame for mp3s.

What is the sample rate?  Is that related at all to bitrate?

Thanks.

---

### Post by Steveway on 2007-08-15
Yes sorry, the version in the repositories is compiled without mp3 support, so the command I gave you will not download libraries needed for a compilation with mp3 support.
You need to type: 
sudo apt-get install liblame-dev 
and 
sudo apt-get install eyed3
and
sudo apt-get install libmad0-dev
That sould install needed files for compilation with mp3 support.
After that you need to compile it again with
./conifgure
make 
sudo make install or sudo checkinstall if you have that installed.
EDIT: Added a .deb I made with ceckinstall, no guarantuee whatsoever and no wma or mp4 support.

---

### Post by Yes on 2007-08-15
Ok, I did all that, and it seems to be working, thanks.

And there still is no way to lower the bitrate to less than 45?

---

### Post by Steveway on 2007-08-15
In the Server-tab where you can change the settings for OGG should now be a Label mp3, click it and change the number from 128 to what you want.

---

### Post by Yes on 2007-08-15
Ok, apparently I hadn't installed those things correctly.  Anyway, I ran those commands again, and it worked, I can now use mp3s.

Thank you for all your help, you've been great.

---

### Post by Steveway on 2007-08-15
No Problem.
Don't forget to add a [Sloved] to the tiltle of your first post.

---

### Post by Yes on 2007-08-25
Unfortunately, I seem to have some more trouble.  For the higher quality bitrate, the "Server Connect" button is blanked out.  I.E., you can't click it.  With the lower bitrate, I can click the button, but when I try connecting, it says "A connection to a radio server failed."  Any idea what the problems might be?

Thanks.

---

### Post by StephenF on 2007-08-26
> **Yes said:**
> Unfortunately, I seem to have some more trouble.  For the higher quality bitrate, the "Server Connect" button is blanked out.  I.E., you can't click it.  With the lower bitrate, I can click the button, but when I try connecting, it says "A connection to a radio server failed."  Any idea what the problems might be?
Thanks.
It's blanked out because you chose a bad combination of settings which the encoder is incapable of handling. Try using a sensible sample rate and enable stereo. As for the connection failure you obviously did something wrong like not setting the port number correctly but there is no way anyone here can help you without a screen shot of the server window and the server configuration file.

---

### Post by Yes on 2007-08-29
Ok, I changed some settings, and now I can click on the high bitrate server's connect button.  I stil get the error when I try connecting, though.  I didn't know there was a server configuration file, I'll go check that out.

---

### Post by Yes on 2007-08-31
Where would the configuration file be?  I'm having a little trouble finding it.

Thanks.

---

### Post by Yes on 2007-09-02
I don't know what I did, but I don't get the error anymore.  Instead, the circle in the tab turns yellow and the program crashes.  

When I start the programs, it says something about the plugins for playing flac are not installed, would you still like to continue (Sorry I can't tell you exactly what it says, I'm not at home right now).  Could this also be a problem?  

Thanks.

---

### Post by Yes on 2007-09-09
Bump.

---

