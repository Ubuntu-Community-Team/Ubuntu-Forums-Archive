---
title: "Can`t find how to copy video to pc..."
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by gasgasohlins on 2007-11-21
I`ve searched for the last 2 hrs reading various threads. Bearing in mind this is a beginners forum,I found the program Kino mentioned in another thread. I activated it as it were and it has shown up in my list of applications. I opened it  and connected my digital video camera(Panasonic NV-GS120). My laptop is an older model where I access my firewire cable via a pc card in the slot at the side of the pc.The whole setup was working fine with XP`s own` Movie Maker` program before I switched completely to Ubuntu.

    Again from another thread,which was about the same thing,a poster there said that if the you get to the `capture` part of Kino and after clicking on same if the  `play`buttons etc were greyed out,to go to preferences.Here, I was to click on the tab displaying `EEEI 1394` and make a choice or add my camera. This is as far as I can get to as when I click I get `The raw1394 module must be loaded and you must have read and write access to /dev/raw1394`

This is where I am confused. As an alternative  I installed dvgrab but when I click on my `applications` it is nowhere  to be found...d`oh!!....

Can anyone point this newbie in the right direction please???....(in an uncomplicated manner!!!)

:)

---

### Post by xpod on 2007-11-21
Not sure if your using Ubuntu or Kubuntu here but you could try starting kino with root privalages by starting it in the terminal with
```
gksudo kino
```
if Ubuntu or...
```
kdesu kino
```
If it`s Kubuntu

That should give kino the relevant permissions to do as it needs...i think:)
IF it`s Ubuntu you can just use ALT-F2 for executing commands rather than the terminal/konsole itself.A bit like the run box in Windows.
I cant recall if Kubuntu does the ALT-F2 thing though.

You can start dvgrab in the same way by just starting it in the terminal.
Or with ALT-F2
Or you could create a launcher.
I have occasionally had menu entries not show up till after X has been restarted i think.

EDIT:I have never used kino myself  so dont know about it but it sounds as though it just needs relevant permissions

---

### Post by gasgasohlins on 2007-11-21
Thanks for responding XPod....I`m running Ubuntu and I did as you suggested...it did show the `play` buttons etc as not being grayed out but nothing else worked when I clicked it. I closed Kino then reopened it and tried the same method as you suggested. Instead of starting Koni by way of a terminal command(like last time) it just says `Error bad device,invalid or uninitialized input device 156` along with `major op code 146,Minor op code 3.Resource ID 0x0. Failed to open device. I re-installed the whole program by way of synaptics to no avail...same message in terminal....any thoughts??....:)

I thought I was onto a winner when the icons appeared in black!!! d`oh!  (By the way the camera is set to  `playback` mode  and turned on)

---

### Post by xpod on 2007-11-21
> Thanks for responding XPod....I`m running Ubuntu and I did as you suggested...it did show the `play` buttons etc as not being grayed out but nothing else worked when I clicked it. I closed Kino then reopened it and tried the same method as you suggested. Instead of starting Koni by way of a terminal command(like last time) it just says `Error bad device,invalid or uninitialized input device 156` along with `major op code 146,Minor op code 3.Resource ID 0x0. Failed to open device. I re-installed the whole program by way of synaptics to no avail...same message in terminal....any thoughts??....

I thought I was onto a winner when the icons appeared in black!!! d`oh! (By the way the camera is set to `playback` mode and turned on)

This was your original problem i now know so not sure it will still help anymore at all?
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

I`ve been trying with an older "Sony handycam dcr-hc4e" to get the movies off the little tapes & onto cd for someone,with just usb......i need to get myself one of those firewire cards too now i think.:)
Plugging it in via usb was no good at all and i did`nt have the time to mess about. 

I had to slink off to XP as the wifes friend wanted the cd to give to someone the same day.Even though i managed though there was far too much loss of quality for it to have been even worth the bother with usb from those tapes.

Mabey someone else can tell you more than me.

---

### Post by gasgasohlins on 2007-11-22
OK thanks Xpod....I now don`t have the option of xp...so it has to be done with ubuntu...I`ll have a wee peep and see what can be done....terribly frustrating I`d say:(

---

### Post by gasgasohlins on 2007-11-22
Tried the link you gave to no avail...I can change some stuff but from then on as it says what should happen does`nt...

:confused:

Probably just me....anyone else like to give it a go??

:)

---

### Post by natehatewindows on 2007-11-22
im a little lost here i think but....

do your firewire ports work in ubuntu? maybe post lspci?

does your camera show up in ubuntu when its plugged in?

---

### Post by natehatewindows on 2007-11-22
and maybe you need some kind of firmware installed? im not sure bt i think there is a good chance,

---

### Post by gasgasohlins on 2007-11-23
Natehatewindows...thanks for the reply...I don`t really know what you mean,sorry,is that something above software,that should be inside my PC?....drivers or such like??......anyway...my camera does not show up on anything when I plug it in and turn it on...in Kino DVD  app. by going through what was suggested before ie edit-preferences-i can get so far as getting the grayed out button in `Capture` mode in the main window to show normal colour. When I click on this it will always say,in the bottom left hand of window`waiting for camera` and do a 10 second countdown to zero where it`ll show failed after that. I now have no idea where to go from here after reading all the threads relative to same...is there another application(jeepers I`m becoming assimilated...I`m starting to call them applications now instead of programs...lol) that I  can use to double check with??
:confused:

---

### Post by gasgasohlins on 2007-11-24
....when i try sudo dvgrab it says theres no camera detected...how can i get it detected???.....

:KS

---

### Post by elctb on 2007-11-24
> **gasgasohlins said:**
> The raw1394 module must be loaded and you must have read and write access to /dev/raw1394`

This is the problem. The 1394 module is a kernel driver that allows you to use the firewire card on your pc. 
Unfortunately, not all firewire cards are supported by linux (but most are, and hopefully yours is). 
You can try the following:
. Open a terminal and find out if there's a 1394 module already installed in your pc. You can use this command "find /lib/modules -name \*1394\*.ko"
. Load the module into the kernel with the command "sudo modprobe <module-name>". Note, remove the .ko at the end of the module name on the modprobe command.
. Give read and write access to the /dev/raw1394 device "sudo chmod 666 /dev/raw1394"
. Now kino should be able to detect your camara.

---

### Post by gasgasohlins on 2007-11-24
elctb..thanks for replying...now bearing in mind `i`m a newbie and crap...lol........help me out in this one...I did as you suggested and got a list of `modules`(about 12 or 15 of them). I picked 3 of them and typed into my terminal(I take it thats what you meant when you said `load module into kernel`??) and the response it gave me was `not found`...or `no such file or directory`I take it thats what you meant for me to do so far?

:)

---

### Post by elctb on 2007-11-24
All these commands need to be typed on a terminal:

. sudo modprobe ieee1394
  sudo modprobe raw1394
  These commands will load the firewire modules you need.

. sudo chmod o+rw /dev/raw1394
  This command gives users read/write access to the /dev/raw1394 device.

Connect your camcorder to the firewire port and don't forget to turn it on. It can't be detected if it's off. Start Kino and verify the camcorder is found. If any of the above commands fail, post the exact errors you get.

---

### Post by heracles on 2007-11-24
worked perfect thanks for your trouble

---

### Post by gasgasohlins on 2007-11-27
[IMG]http://img.photobucket.com/albums/v112/CorpClinger/Screenshot-2.png[/IMG]

This is all I`m getting....any thoughts???....


:confused:

---

### Post by elctb on 2007-11-27
I'm not sure where the bracken command is coming from. Are you typing it ?

For the chmod error, make sure there's a space between o+rw and /dev/raw1394

```
sudo chmod o+rw /dev/raw1394
```

---

### Post by gasgasohlins on 2007-11-27
Good morning or good evening ...what ever it is elctb!!!....I tried as you can see to type in what you suggested...the `bracken` word as you can see on the screenshot is what I typed in(after being prompted,ie,my password)for my PC....I have just tried typing in all that you suggested only to find that now I`m not prompted for my password!!!...as Homer says `D`oh!!`....Its interesting to see that another member of this board has replied and all has worked for him,ie Hercales...mmm...something afoot with my installation of Ubuntu???....(I installed from a CD that they sent out to me)...mmm...baffling or what...after all your instructions seem to be set in concrete(due to them working for Hercales)...any thoughts anybody..anywhere???...


:confused:

---

### Post by WinterWeaver on 2007-11-27
Prob the first, next step is to change your password.... :popcorn:

---

### Post by elctb on 2007-11-27
sudo has a timeout and remembers for a while your password so that you don't have to enter it every time. After a few minutes it times out and then it asks for the password again.

If the modules loaded without errors and you changed the permissions of /dev/raw1394 without errors, you are ready to connect the camcorder to the firewire port. Make sure you turn it on and set it to playback, rewind the tape but don't press play yet.

Start kino, click on edit -> preferences -> ieee 1394

and check is your camcorder is detected.If it's not, post the information on the screen.

If it's detected, you can click on capture and play to transfer the video to the hard drive.

I would do as WinterWeaver suggests and change the password.

---

### Post by gasgasohlins on 2007-11-28
Half working!!!... I did as suggested and changed password(after a wee search for how to do it)...I typed in the sudo directions as listed above...and got the 1st screenshot....I opened up Kino and it auto detected the camera.... I checked in preferences and it stated the camera was indeed a Panasonic etc....so I clicked on capture and I was able to see moving images on my PC...but,lo and behold,1 second later a mini window opens with it saying `Failed capture,is the file name OK?`  or words to that effect....I click on OK and the mini window returns after every one or two seconds of recording...with no video downloading. So,I close Kino and try it all again right from the sudo directions but on the second go I get this 2nd screenshot window.  I notice too now that Kino has reverted back to No camera detected etc

     .What I would say is that although I got the 1st screenshot messages they must have loaded somewhere along the line to allow Kino to try and capture the video. I have tried again doing everything from the start to no avail. I know that I am almost there with this. Any directions folks...it does seem to be straightforward enough by this stage but I`m at a loss....Its almost as if my terminal is`nt working properly??....:confused:

Screenshot One....
[IMG]http://img.photobucket.com/albums/v112/CorpClinger/Screenshot-1-1.png[/IMG]

Screenshot Two
[IMG]http://img.photobucket.com/albums/v112/CorpClinger/Screenshot-2-1.png[/IMG]

---

### Post by gn2 on 2007-11-28
One sure fire solution to your problem is to connect your camera to a stand-alone DVD Recorder with a suitable connector and transfer the footage direct to a DVD-RW.

It can then be ripped to the PC and edited as desired.

Costs a bit for a DVD Recorder if you don't already have one, but it gives you added functionality.
........you can't record TV on a Firewire card ;)

---

### Post by elctb on 2007-11-28
On the first screen, you mistyped the device name "/devraw1394". It should be "/dev/raw1394"

Just to be sure use this command to change the permissions instead:

```
sudo chmod go+rw /dev/raw1394
```

Again connect the camcorder and make sure it's on. Most camcorders turn off automatically after a while so always make sure the camcorder is on when trying to capture to the pc. Set the camcorder to play and rewind the tape.

Start kino and configure it:
```
. Preferences:
            . Audio:
	        . Select 48 KHz.
	    . Capture:
	        . Enter base file Name (hawaii-vacation-2007- or whatever). Captured files
		  always get saved in your home directory
		. File type: Select dv2. This will create avi files. However, they not always 
                  load on cinelerra. If you are using cinelerra for video editing select the 
                  File type as "Raw DV"
		. Select auto split files to have each scene on a separate file.
		. Write every: 1 frame
		. Frames per file: 7000
		. Max file size: 2000 MB
```

Then select capture.

If kino can't detect the camcorder all of the sudden, make sure the camcorder didn't shut itself off.

---

### Post by gasgasohlins on 2007-11-29
Sorry about fluffing such a basic instruction as a typo after you`d taken so much time to help...

    Anyway...onwards and upwards as they say...I changed the preferences as suggested...and still  no luck with the camera be detected...strange after it had been detected last time and all that...anyway...this screenshot shows what I got once I loaded in the new sudo stuff...I went back to the start of the thread and tried some stuff there also...no deal...I wonder what can be happening in respect of the fact that I got it half working last time....??syas no such file or directory..back to square one???


[IMG]http://img.photobucket.com/albums/v112/CorpClinger/Screenshot-3.png[/IMG]

---

### Post by elctb on 2007-11-29
It looks like the raw1394 module is not loaded. This module is the one that creates the /dev/raw1394 device. Remember that you have to manually load the modules every time you reboot the machine. Therefore, run these 2 commands before anything else:

```
sudo modprobe ieee1394
sudo modprobe raw1394
```

and then:

```
sudo chmod go+rw /dev/raw1394
```

Then connect the camcorder and follow the instructions on my last post.

---

### Post by gasgasohlins on 2007-11-29
Again...thanks....I rebooted my pc just to be sure and the first thing I did when it started was to open the  terminal as can be seen and typed in what you`d mentioned....followed the instructions and no detection of camera noted.(even did the change password thing again!!)... When I opened the terminal should I see something more,like perhaps a list of things getting loaded or suchlike??.....this is all that happened...normally should I at least see my password getting shown??...The commands weretyped in after each other,I opened Kono manually and still no change....weird yes/no?? Synaptics problem??....I just don`t know...aaagggghhhhh!!!...lol

Anyway...time to give up and accept that I just can`t get Ubuntu to work with my camera??What do you think....you`ve been very patient and I don`t want to lumber you with my newbie trivial problems
:(


[IMG]http://img.photobucket.com/albums/v112/CorpClinger/Screenshot-5.png[/IMG]

---

### Post by elctb on 2007-11-29
OK. Let's try one more thing. After you enter the 3 commands:

```
sudo modprobe ieee1394
sudo modprobe raw1394
sudo chmod go+rw /dev/raw1394
```

Start kino as root with the command:

```
gksudo kino
```

---

### Post by gasgasohlins on 2007-12-04
Its actually worked!!!..I left the pc off for a couple of days whilst away for the weekend...tried it again this morning following the instructions in the last post and it worked.....Thanks so much to all for responding...its a credit to the forum and to yourselves...(esp elctb for sticking with it)

    I can now email a video shoot of my son his bicycle to his Grandparents,all the way from France to Ireland...(or will that be the subject of another thread...:)   )Thanks  again to all


:guitar:

---

