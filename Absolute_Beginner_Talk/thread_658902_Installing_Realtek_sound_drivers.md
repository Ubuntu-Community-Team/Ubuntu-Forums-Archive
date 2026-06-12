---
title: "Installing Realtek sound drivers"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Aqualung on 2008-01-05
I just downloaded the Realtek Linux drivers from the Realtek website, and I wanted to install the sound drivers for my mobo-embedded ALC888 sound chip. The readme file says I should execute ./install for an "Automatic install," which is precisely what I did, with all the permissions required and all that jazz. The result of running the ./install file, however, contains lots of negative statements like "configure: error: C compiler cannot create executables," "install: cannot stat `include/sound/*.h': No such file or directory," "./snddevices: not found" etc. (see below in detail), which makes me wonder whether the drivers got installed after all. The difference from the "before" state is almost zero; among others, the sound settings window keeps making reference to an ALC883 instead of ALC888 .

What am I doing wrong?

Here's now the detailed result of running the ./install file:

sudo ./install
.....Decompress Driver source v1.0.15rc3-4.07a
.....Decompress ALSA Library source v1.0.14
.....Decompress ALSA Utility v1.0.14
Remove old sound driver
Compile Driver........
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
make all-deps
make[1]: Entering directory `/home/cristi/Desktop/realtek-linux-audiopack-4.07a/alsa-driver-rt20071002'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/cristi/Desktop/realtek-linux-audiopack-4.07a/alsa-driver-rt20071002'

Please, run the configure script as first...

if [ -L /include/sound ]; then \
                rm -f /include/sound; \
                ln -sf /home/cristi/Desktop/realtek-linux-audiopack-4.07a/alsa-driver-rt20071002/include/sound /include/sound; \
        else \
                rm -rf /include/sound; \
                install -d -m 755 -g root -o root /include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /include/sound; \
                done \
        fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
./install: 39: ./snddevices: not found
Remove old alsa library
Compile ALSA Library.....
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Compile ALSA Utility......
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
cp: cannot stat `/usr/lib/libasound.*': No such file or directory
cp: cannot stat `/usr/lib/pkgconfig/alsa.pc': No such file or directory
Remove Folder.....
./install: 100: alsaconf: not found
cristi@SpongeBob:~/Desktop/realtek-linux-audiopack-4.07a$

---

### Post by exneo002 on 2008-01-05
hey I have a realtek on board and I just gave up on it you should just buy a linux friendly sound card 
 but If you find an easy way to do it just email me at [email]exneo.socomplayer@yahoo.com[/email]

---

### Post by kellogs908 on 2008-01-05
same problem here
in my post there is somehelpful info but i havnt been able to get it to work yet
[http://ubuntuforums.org/showthread.php?t=658634&page=2](http://ubuntuforums.org/showthread.php?t=658634&page=2)
there are several links posted by other users which are helpful for going through a list of possible problems, once I figure this out, if I do, I will be sure to make a tutorial on how to fix the issue because the issue seems apparent with several users

---

### Post by blithen on 2008-01-05
You need to make sure you have build-essential installed

```
sudo apt-get install build-essential
```

---

### Post by aktiwers on 2008-01-05
Have you guys checked this?
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If it seams confusing, try post the output of:
```

cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by SidewinderPro2 on 2008-01-05
Theres a really good chance that you are not using a Realtek onboard card. Mine uses the drivers/codecs, but its an Nvidia chipset. I downloaded the Realtek HD audio codecs for Linux, installed them, and got nothing. I then spent a great deal of time messing with the ALSA modprobe file, and then did this, for my nForce 430 chipset:

Find yours here: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

Mine: [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

Find your card, then click the Details link in the table that list different models of your particular brand. Follow the instructions. At the end it has you run the alsamixer. Try to make sure the speakers are unmuted in the alsamixer, it kinda helps...:lolflag:

Sound setup for anything that uses the Realtek codecs is a massacre.

---

### Post by Aqualung on 2008-01-05
Now lemme tell you what the funny thing is: my soundcard works perfectly fine (or, at least, I *have* sound) with the *default* drivers installed by the Ubuntu setup. Can't complain about that--unlike, I assume, the rest of y'all. I am just trying to exert my ol' Windows habits by checking with the manufacturer website for the newest drivers: I don't really trust the drivers downloaded by Windows Update... Now, it looks to me, however, that I may have to drop this habit in the Linux world, as manually installing drivers looks to me to be an incredibly cumbersome venture, fraught with peril. I'd rather let Ubuntu install whatever it wants to, as long as things work. Don't fix it if it ain't broken, as they say... This, it seems to me, should be something one should stick with in the Ubuntu/Linux world. As far as Windows goes, I always install the newest and greatest drivers, regardless of whether the old ones work fine or not. :)

Otherwise, I wish there were a nice Windows-like method to tell what driver version each one of my PC's devices have. I don't know to what extent one should trust the default Ubuntu Driver and/or Update Managers to have the latest drivers: e.g., it looks to me that my nVidia videocard drivers are not really the latest at this point in time (although things work fine so far, can't complain); I am pretty sure that Nvidia has newer Linux drivers on their website than the ones installed on my PC. (Btw, what is the usual time interval within which Ubuntu driver repositories get updated with the latest officially released Linux drivers? What can we, end users, do to speed up this process? Is there some way we could signal Ubuntu officials that a newer Linux driver for a particular device, has been released?)

Hence, how can I tell what driver version is installed for a particular device? How can I tell what driver version my soundcard has now?

---

### Post by FuturePilot on 2008-01-05
The drivers in the repositories only get updated every 6 months when a new release of Ubuntu comes out. It would be too risky to try and update the drivers in the middle of a stable release. It could cause lots of breakage. 

I'm pretty sure the drivers for you sound card are the Alsa 1.0.14 drivers.

---

### Post by Aqualung on 2008-01-05
> **SidewinderPro2 said:**
> Theres a really good chance that you are not using a Realtek onboard card. I built my computer myself: the mobo is a Tyan S2696 (a Woodcrest-based dual Xeon), whose one and only sound chip is an ALC888 (Realtek).[quote=FuturePilot]I'm pretty sure the drivers for you sound card are the Alsa 1.0.14 drivers.[/quote]How about that method I was asking about: how can I tell what driver version my nVidia videocard has, say?

Thanks for the replies.

---

### Post by Aqualung on 2008-01-05
> **aktiwers said:**
> ... post the output of:
```
cat /proc/asound/card0/codec#* | grep Codec
```Here's the result: Codec: Realtek ALC888 -- and this with the *native/default* Ubuntu drivers, i.e. before any attempt to "install" the ones I downloaded etc.

---

### Post by aktiwers on 2008-01-05
Okay then you need to follow that Wiki I posted.

Start following "Update to the Latest Version of ALSA" part.

Then under "Manually Specify Module Parameters" we need to look up your card.

This is how it looks:
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt#850](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt#850)
> ALC883/888
          3stack-dig    3-jack with SPDIF I/O
          6stack-dig    6-jack digital with SPDIF I/O
          3stack-6ch    3-jack 6-channel
              3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
          6stack-dig-demo  6-jack digital for Intel demo board
          acer        Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
          medion    Medion Laptops
          medion-md2    Medion MD2
          targa-dig    Targa/MSI
          targa-2ch-dig    Targs/MSI with 2-channel
          laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
          lenovo-101e    Lenovo 101E
          lenovo-nb0763    Lenovo NB0763
          lenovo-ms7195-dig Lenovo MS7195
          6stack-hp    HP machines with 6stack (Nettle boards)
          3stack-hp    HP machines with 3stack (Lucknow, Samba boards)
          auto        auto-config reading BIOS (default)

So basicly we need to change the ones from the wikipage to the same as yours. If one of the laptops are same model or almost same as yours Good - change the MODEL in 
/etc/modprobe.d/alsa-base

Line 

options snd-hda-intel model=MODEL

And save the file.

If this doesnt work, you will need to try some of the other ones. I found that one model that didnt match the machine was the only who worked.

If what I am typing is complete nonsens, please let me know, then I will try to explain a little better. :)

---

### Post by laceration on 2008-02-03
I just built a new Ubuntu machine.  The sound did not work.  I searched these forums, the solutions gave me a headache.  Isn't Ubuntu supposed to be easy to configure?  I tried the easiest solution first, from the posts from aktiwers, and it really was simple.  It took only 3 steps!  The hard part was getting through all the verbiage.
 Here's how I did it( I'm repeating info from aktiwers, only to make it clearer and simpler and in 1 place):

What I didn't do: I did not download or recompile the latest ALSA.  Why bother?  It turns out I didn't need to do that, why hassle with it if you don't have to.

**Step 1:** Applications->Accessories->Terminal.  At the prompt paste in:
cat /proc/asound/card0/codec#* | grep Codec
it'll return something like, Codec: Realtek ALC888

**Step 2**: Go to [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt")
Find your Codec.  There is a list of model name and  descriptions for each Codec starting on line number785.  Copy the model name you've got.  For me it was 6stack-dig.

**Step 3:** Again at the terminal type sudo gedit /etc/modprobe.d/alsa-base
Provide pw when prompted.  Add at the end of file: options snd-hda-intel model=6stack-dig
Of course with your model in place of 6stack-dig.  Save the file.  That's it!

Now I even have digital sound coming through the spdif:guitar:

---

### Post by Aqualung on 2008-02-03
Thank you for the feedback, but I am still confused: So far none of you makes any reference to the drivers I downloaded from Realtek's website. What are those for? Shouldn't *that *be the main driver source? Drivers sanctioned by *the manufacturer itself*? Why do they bother posting them, if noone uses them?

---

### Post by aktiwers on 2008-02-04
Thanks for clearing it out. Now when I reread my post, I see it was a bit confusing.

Aqualung - Please try following the 3 steps. It's true you don't need to compile the newest alsa drivers, as Gutsy has uptodate Alsa.

My knowledge of the difference between alsa and the realtek drivers is pretty limited, but as I understand it, Ubuntu already support your card and a driver is installed. Alsa is the soundserver(controlling the sound) and by default Ubuntu has some trouble defining the right model.

Thats why you need to go into /etc/modprobe.d/alsa-base and specify it.

I'm not 100% sure, but I think thats the reason for this.
But try it, I'm sure it will work :)

---

### Post by sabry_lk on 2008-06-20
thanks soo much!!!! 
surround sound worked on ALC888 after i followed these instructions... was breaking my head over getting it to work for a long time!

---

