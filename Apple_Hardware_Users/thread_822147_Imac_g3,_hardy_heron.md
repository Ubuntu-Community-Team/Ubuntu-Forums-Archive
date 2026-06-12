---
title: "Imac g3, hardy heron"
date: 2008-06-07
forum: Apple Hardware Users
---

### Post by Mariofreak64 on 2008-06-07
I got a version of hardy heron for powerpc, and intalled it with no problem on my g3(350 MHz, 256 ram, slot loading) but when it tries to boot, it goes threw the boot strp, then goes to a white screen with some text, a black Screen that says, "Loading, Please wait" Then it makes sounds of the computer shutting down (screen buzz, etc), and the screen is black, no sound, and the power light is still on. I used the text based installer.

---

### Post by avtolle on 2008-06-08
Can you get to the terminal once you are at the "end state" you describe (Alt+Ctrl+F1)? It sort of sounds like there will be a need to edit your /etc/X11/xorg.conf file to get you up and running. You might want to search this forum for other tales concerning G3s, and what steps that needed to be taken to get a GUI.

---

### Post by Mariofreak64 on 2008-06-08
> **avtolle said:**
> Can you get to the terminal once you are at the "end state" you describe (Alt+Ctrl+F1)? It sort of sounds like there will be a need to edit your /etc/X11/xorg.conf file to get you up and running. You might want to search this forum for other tales concerning G3s, and what steps that needed to be taken to get a GUI.
So after the screen turns off? I'll try to get a pic of the white screen

---

### Post by Mariofreak64 on 2008-06-08
> **Mariofreak64 said:**
> So after the screen turns off? I'll try to get a pic of the white screen

the white screen says

done
copying OF device tree...
Building dt strings...
Building dt structure...
Device tree strings 0x022da000 -> 0x022dab68
Device tree struct 0x022db000 ->0x022ef000
Calling quiesce ...
returning from prom_init

than it goes to loading, then turns off

---

### Post by avtolle on 2008-06-08
Yes, after the screen "turns off". I think the white screen to which you refer is the same one I get when I'm booting (or similar), which contains some text, then goes to a black screen, which, in my case, is then occupied by the "spinner" which eventually leads to the log in page (I'm on G4 Cubes, BTW, so likely is a bit different). When I first installed, could not get to the log in page, cured by manually editing the /etc/X11/xorg.conf file, which is why I was inquiring about your ability to get to a terminal.

---

### Post by Mariofreak64 on 2008-06-08
> **avtolle said:**
> Yes, after the screen "turns off". I think the white screen to which you refer is the same one I get when I'm booting (or similar), which contains some text, then goes to a black screen, which, in my case, is then occupied by the "spinner" which eventually leads to the log in page (I'm on G4 Cubes, BTW, so likely is a bit different). When I first installed, could not get to the log in page, cured by manually editing the /etc/X11/xorg.conf file, which is why I was inquiring about your ability to get to a terminal.

It won't come up. It really sounds like the hardware shuts off, because it makes that crt turning off buzz

---

### Post by avtolle on 2008-06-08
Before it "turns off", can you get to a terminal (at some point in the process that's what I had to do)? If so, then you may be able to edit the xorg.conf file. For what to edit it to, there are some threads showing working xorg.conf files for g3s in this forum, for which you will need to search (sorry, don't have them bookmarked). First, though, you will need to get to a terminal; perhaps booting into Linux Single User at the second prompt can get you there (hit Tab to give you a bit of time).

---

### Post by Mariofreak64 on 2008-06-08
> **avtolle said:**
> Before it "turns off", can you get to a terminal (at some point in the process that's what I had to do)? If so, then you may be able to edit the xorg.conf file. For what to edit it to, there are some threads showing working xorg.conf files for g3s in this forum, for which you will need to search (sorry, don't have them bookmarked). First, though, you will need to get to a terminal; perhaps booting into Linux Single User at the second prompt can get you there (hit Tab to give you a bit of time).

I tried at numerous points in start-up, and it never worked. Should i just go back to dapper drake?

---

### Post by avtolle on 2008-06-08
At the second yaboot prompt, hit <tab>, then type Linux single <return> and see what that gets you. In my case (admittedly, with graphical interface otherwise running), it takes me to a "rescue" menu, upon which there are, among the four choices, root bash prompt and Try to fix x (or words to that effect). I don't know what happens if you don't have your graphics able to run, but from a post on another thread, I inferred it would drop one into a CLI  where one could issue terminal commands.

---

### Post by stream303 on 2008-06-08
Exactly - we've got to get you to a point where you can edit your xorg.conf to accurately reflect the changes needed for your vertical and horizontal frequencies.  They are detailed here for the G3 iMacs:

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

If your dapper-drake is a live-cd, you might have an easier time getting to a terminal or use gedit (either sudo nano -w /etc/X11/xorg.conf, or in a gui, gksudo gedit /etc/X11/xorg.conf)

---

### Post by applefat on 2008-07-10
I'd like to add that the same thing happens when I try to boot from my imac slotloading g3, 400mhz with 512mb ram. About 20 seconds in it just makes the "monitor turning off" sound, and there is no cd-rom activity, no hdd activity, but the power light is still on.

Same as the OP, there's no real place to get to the prompt before this happens.

---

### Post by calking on 2008-07-21
Yes that's true. But the OP wanted to use Hardy Heron. I managed to get to the xorg.conf of the live cd for Hardy Heron, but the conf is completely different than dapper and doesn't list the monitor info needed for using the GUI. If the xorg.conf file for heron is available here someone could look around and figure out what needs to be changed in order for X to operate. It would appear that X crashes and closes because when the killall is given in the imac g3 monitor cutoff tutorial, theres no program to run. When I attempt to restart X, I get some no screens found error.

---

### Post by stream303 on 2008-07-22
That link earlier on, shows the additions you'll need to make in Hardy's xorg.conf.  Find the **monitor** section, and put in those vertical and horizontal frequencies, and also put in that module section which disables glx and dri.  Unlike the old xorg, Hardy's is pretty much blank, so we'll have to just add them in manually.

Looks like the only way to do it is to get to the cli by interrupting yaboot so that it doesn't try to load xorg.

At the second stage of the yaboot: boot prompt, hit -tab-.  This will stop the countdown, and you should be presented with some options.  One of them should be:

```
rescue-powerpc
```

If you type that in, and eventually choose /dev/hda3 as your root shell, (or whatever is your root partition), you can edit /etc/X11/xorg.conf with vi or possibly nano.

---

### Post by coreno on 2009-02-06
Has anyone found a solution to this problem? I am having an Identical problem, but with Intrepid Ibex (8.10).

I had to use the rescue mode on the CD to try and edit the xorg.conf file because most people seemed to point to that being the issue, but my xorg.conf was blank.

I tried to add information based on other g3 xorg.conf files I found on the web, but it didn't seem to work.

I can confirm the mac is shutting down, or at the very least going to sleep. I can hear the harddrive power off, and if the CD is spinning, it spins down as well. The power light also dims, but does remain on, suggesting some sort sleep mode.

Any assistance MUCH appreciated :)

---

### Post by Cyanaether22 on 2009-02-06
Exact same problem here only using Intrepid. I'm sure that xorg.conf is the problem but there doesn't seem to be a way to get at it for editing. I managed to get at it in repair mode but couldn't figure out how to edit the file using the command prompt.

---

### Post by avtolle on 2009-02-07
> **Cyanaether22 said:**
> Exact same problem here only using Intrepid. I'm sure that xorg.conf is the problem but there doesn't seem to be a way to get at it for editing. I managed to get at it in repair mode but couldn't figure out how to edit the file using the command prompt.
At the command prompt, do```
cd /etc/X11
ls
```to see a list of files. If there is a file called xorg.conf.failsafe (or something similar) do (again from the command prompt)```
sudo cp xorg.conf. failsafe xorg.conf
```to copy the structure for the file. Then, from the command prompt do```
sudo nano xorg.conf
```to open the file for editing. Once in the file, make the changes to the file suggested by other threads. Upon completion, Ctrl+o to write the file as changed, Return to accept the default file name (should be xorg.conf), then Ctrl+x to exit the editor. At this point, restart your computer to see if this gets you somewhere.

On my G4 Cubes, after editing the file to suitable parameters, the restart brings up an error message and then after clicking OK or continue (I don't recall which) another box with options appears; choose Use low graphics (or safe graphics) for this session only; another box appears that indicates the screen is restarting, hit OK, and, fingers crossed and breath held, the sign-in page will appear. Enter the username and password, and the desktop will come up (hopefully for you; it does for me). Again, in my case, the desktop comes up in an appropriate resolution, notwithstanding the "use low graphics" message earlier appearing. From there, you can proceed to do whatever it is you need to do (in my case, update) and then try to tweak the /etc/X11/xorg.conf file for your computer. Sorry for the rambling nature of this. Good luck.

BTW, a side note; I'm also trying openSUSE 11.1 on my Cube reserved for playing, experimentation and breaking things. It comes up without issue in the right resolution, etc. without the need to edit the xorg.conf file. Had the same experience with Yellowdog when I tried it out.

---

### Post by avtolle on 2009-02-07
Or, you may just, from the command prompt, do```
sudo nano /etc/X11/xorg.conf
```and copy the appropriate information into the otherwise blank file from that posted in other threads for imac g3s; the operative stuff is the display, monitor, etc. (the keyboard, font paths, mouse, etc. information is now apparently handled by HAL, as nearly as I can tell), then save, etc. as described above.

Have you tried, at the second stage of yaboot, hitting TAB to slow down/stop the booting process, and at the boot: prompt entering Linux video=ofonly there? That's something else you might try if you haven't. Again, good luck.

---

### Post by Cyanaether22 on 2009-02-07
Thanks for the help mate! Unfortunately when I typed in sudo nano xorg.conf (when i was in the X11 folder), it said...

Error opening terminal: bterm

Any pointers? i'm going to research that error.

---

### Post by Cyanaether22 on 2009-02-07
Alright I did export TERM=Linux and then tried again, nano opened and it's all good.

BUT xorg.conf appears to be blank. It said "0 Lines Read". There doesn't appear to be any backup of xorg.conf or anything else.... can I write the whole file myself?

---

### Post by nkbj on 2009-02-08
There are two bugs in play here. The boot process stops with the system shutting down:
[https://bugs.launchpad.net/ubuntu/+source/linux-ports/+bug/216666](https://bugs.launchpad.net/ubuntu/+source/linux-ports/+bug/216666) and then a problem with xorg.conf: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-r128/+bug/22976](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-r128/+bug/22976)

---

