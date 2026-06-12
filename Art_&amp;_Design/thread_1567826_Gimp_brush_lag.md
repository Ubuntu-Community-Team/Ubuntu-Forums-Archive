---
title: "Gimp brush lag"
date: 2010-09-04
forum: Art &amp; Design
---

### Post by Scayris on 2010-09-04
Hi everyone.

I have a problem. I'm a digital artist and a regular GIMP user. I run Ubuntu 10.04 and use a Wacom Intuos4 tablet to paint. But there's this annoyance that's been bugging me for a while and is just destroying my nerves.

While using a larger brush (radius 20 is more than large enough for this to happen), the brush starts to lag behind the cursor. It can take even a few seconds for the brush to catch up after I finish a stroke. Needless to say, this is VERY annoying and makes it way harder to paint. I don't even see where I'm painting because the brush outline is so far behind the mouse cursor.

The only workaround is to use smaller brushes, but that means my paintings are smaller, I can't make wallpapers nor prints due to small size and even mistakes become more visible. Also, painting details becomes pixel art...

My computer has a 64-bit quad core AMD processor and an ATI Radeon graphics card accompanied by 4GB of ram. I believe it should easily be able to run GIMP without lagging like this.

Now, I've tried to install ATI proprietary drivers, which just made things worse. Disabling Compiz didn't work either. Not even increasing tile cache size to 3000MB and allowing GIMP to use 4 processors did anything for performance.

Now I ran out of ideas. Painting like this is hard and frustrating and I'm really starting to get tired of it. Can anyone help..?

---

### Post by psoulocybe on 2010-09-04
In Gimp's Preferences, go to Image Window, then play with the options in mouse pointers.  Not drawing the brush shape, and only using a simple cursor can help this issue, a little bit.  I've never gotten brush control to the point of MyPaint in Gimp, but this may make it a bit better.

---

### Post by Scayris on 2010-09-04
I tried turning the brush outline off, and while not seeing it is a bit annoying, the lag got noticeably smaller :)

Thank you for the tip! :) This'll surely help with painting larger images. I still wonder how to speed the whole thing up though...

I think my graphics card could be at fault...

---

### Post by Favux on 2010-09-04
Hi Scayris,

You may be running into a known gtk/Gimp bug.  So many stylus/brush inputs that the CPU bogs down.  I'd think your CPU could handle this though.  To check see if changing the RawSample parameter helps:
```
xsetwacom set 9 RawSample "4"  # default is 4
```
to say:
```
xsetwacom set 9 RawSample "20"  # default is 4
```
Raising the parameter decreases the sampling rate.  If this helps, pretty much by definition that's the bug.  Of course you'd use the "Device Names" or ID number's that:
```
xinput --list
```
gives you.

They're working on it and already have a few fixes for it in Gimp.

---

### Post by psoulocybe on 2010-09-04
Favux, thanks again for awesome input.  I did not know there was an existing 'bug' with this, but it's something I've been fighting for months.   I'm going to give it a shot and see what happens.

What do you mean they have a few fixes for it in Gimp?  In the development snapshots, or stand alone fixes?

---

### Post by Favux on 2010-09-04
Hi psoulocybe,

I don't recall exactly what Alexia Death (a Gimp developer) told me a while ago.  I think she said a Gimp side partial fix was already in Gimp and some others were in the Gimp development snapshots.  I gather they've been having trouble with gtk motivating any fixes.

---

### Post by Scayris on 2010-09-05
Hi, Favux. Firstly, thanks for your advice.

I've tried setting RawSample to 4, then to 20 and even 50 for all the wacom input devices (eraser, cursor, pad) using numbers listed under "id=" column. I tried restarting x afterwards too, but performance didn't improve at all... Running the command with -v tells me in the last line that the device was found, but nothing about changing the parameter. I'm not sure it's supposed to though, so now I'm not sure if this wasn't the problem or the command didn't work?

---

### Post by Favux on 2010-09-05
Try the xsetwacom command in a terminal using the "Device Name" with the quotes that 'xinput --list' gives you.  It should apply immediately with no need to restart X.  To check the setting use 'xsetwacom --get', see 'man xsetwacom'.

---

### Post by Scayris on 2010-09-05
Okay, I tried by device name, still no changes.

Oddly enough xsetwacom --get only displays the help page and man page appears to be nonexistent.

---

### Post by Favux on 2010-09-05
Ahhh!  Sounds like you're using the default 0.10.5 xf86-input-wacom that comes with Lucid.  It's up past 0.10.8 with a lot of xsetwacom fixes and additions (including 'man xsetwacom').  Given you're using your tablet professionally you probably should consider updating.  See the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562"), **I. & II**.

---

### Post by Scayris on 2010-09-06
Thanks :)

But the tutorial seems to be for wacom pen and touch tablets, I have an Intuos4 tho.. Is the procedure the same?

---

### Post by Favux on 2010-09-06
Yes, I. and II. install the wacom.ko and xf86-input-wacom.  If you look at the top you'll see I say "And Other Wacom Tablets."  I pointed you there because of the sample xsetwacom scripts attached to the second post.  You could also do Sections 1 & 2 at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1"), as long as you remember not to do "sudo make install" in Section 1 after compiling the wacom.ko.

By the way we have the OLED's working again.  Actually I posted the Intuous4 sample script on the Intous4 thread.

---

### Post by Scayris on 2010-09-06
OLED's too? :o Wonderful :) I almost forgot they existed, not using them for so long :)

I do wonder however.. Maverick comes out in a month and I'll be doing a clean install soon, so are the new drivers already included in it or will I still have to do this to get them?

---

### Post by Favux on 2010-09-06
> Maverick comes out in a month and I'll be doing a clean install soon, so are the new drivers already included in it or will I still have to do this to get them?
Good question.  I don't know.  You'd want to have at least 0.10.8 xf86-input-wacom and I don't know what Maverick is currently using as it's default.  Plus the kernel maintainer has been blocking the latest linuxwacom wacom.ko's because they aren't compliant with the new multi-touch protocol.  So I don't what version the 2.6.35 kernel has.  Linuxwacom wrote the Bamboo multitouch/gestures stuff before the new protocol came out and now they'll have to rewrite all that.  I think the first test case, for the Bamboo touch, was just accepted (committed).  So at a guess still more fiddling with 11.4 as finally the Holy Grail.

---

### Post by Scayris on 2010-09-21
Ah, okay then.. Would the installation procedure be the same on maverick? Because if so I'll just wait till the final version and test the new drivers out on a clean install.

Also, sorry for the incredibly slow reply...

---

### Post by Favux on 2010-09-21
Hi Scayris,

I installed Maverick beta a week or two ago.  The default xf86-input-wacom is 0.10.8, so not much urgency in updating that.  If the wacom.ko doesn't work, and it doesn't for the new Bamboo Pen and Touches (at least it didn't for me), linuxwacom 0.8.8-8 compiles just fine.  So I've got things working in Maverick and I like how Gimp's behaving so far.

---

### Post by Scayris on 2010-11-13
Well, I'm using Maverick now and the problem remains. The brush is still lagging, exactly as much as before if not more.. I tried the raw sample setting too and nothing changed...

---

### Post by Favux on 2010-11-13
Hi Scayris,

Are you using the correct "Device name" in the xsetwacom command?  What is your current output of?:
```
xinput --list
```

---

### Post by Scayris on 2010-11-13
I used the id number instead of name...

```
scay@scay-desktop:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 eraser               	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 cursor               	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 pad                  	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 stylus               	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]

```

I figured something else out tho. If I run "metacity --replace" the lagging disappears, so it could be Compiz causing it, however, the line becomes jumpy. While I draw the pointer doesn't lag, but the line behind it doesn't render instantly. I draw a line and as I draw parts of the line are appearing like 30 pixels of length at a time. It's happening fast, so it's not really that bad, but it's an annoyance. The line is rendered perfectly too, it doesn't just draw straight lines from one point where the line appeared to the next one. This is definitely better than the lagging brush though...

---

### Post by Favux on 2010-11-13
OK, try with your xsetwacom command something like this:
```
xsetwacom set "Wacom Intuos4 8x13 stylus" RawSample "20"  # default is 4
```
Remember if you are hot plugging the tablet the ID # can change.  In that case you are better off using the "Device name", which won't change.

Sounds like you've found another partial work-a-round by going from Compiz to Metacity.

---

### Post by Scayris on 2010-11-13
I think it's lagging less, but it still is lagging. I've noticed that what causes it more trouble are curves. If I draw let's say 6 circles quickly with a single line the brush will in the end definitely be behind. It's even worse if I try to just quickly scribble something out or colour something in the same way. (talking with compiz on, on metacity it's all great but jumpy)

---

### Post by Favux on 2010-11-13
Well you can adjust from 20 to 25 or 30.  20 was just a good compromise on my system to  minimize lag but keep it from getting too jumpy outside the drawing window.  Your system may be different.  I think actually 40 or higher was best for lag, just not real usable outside the active area then.  The higher number might make tracking a curve more problematic too, I suppose.

---

### Post by jomaksmile on 2010-11-14
Don't recall exactly what Alexia Death (a Gimp developer) told me a while ago. I think she said a Gimp side partial fix was already in Gimp and some others were in the Gimp development snapshots. I gather they've been having trouble with gtk motivating any fixes.

---

### Post by Scayris on 2010-12-15
Hello all. Yeah, I'm back. The problem remains.

After a while I tried working on a bit larger image, namely 2732x1536 pixels. Firstly I'd like to point out that this is still nothing, artists usually work with images larger than 5000x5000, otherwise it's impossible to put in details.

I've set raw sample to 40, even disabled Compiz, but even Metacity is blocking at this size. And I repeat, this isn't half the size I need to be able to work with. Is there anything else that could be causing the slowdown? Any other way to fix it? This is really driving me crazy and this picture is already overdue... Thanks.

---

### Post by Favux on 2010-12-15
Hi again Scayris,

The only thing I can suggest is trying to update your Maverick drivers with the 0.8.8-10 linuxwacom wacom.ko and the 0.10-10 xf86-input-wacom.  Again see the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") parts I. and II.  It's worth checking to see if an updated kernel driver or X driver helps.

There are some fixes that should apply to the Intuos4 coming to xf86-input-wacom soon.

You could also try varying the Suppress setting and perhaps Threshold/ClickForce.  There's an updated script attached to the HOW TO with xf86-input-wacom defaults and ranges for stylus and eraser that you could use.  I'm still working on updating the Intuos4 script I posted on the Intuos4 thread.

---

### Post by djwkd on 2010-12-21
I, too, am having the same problem with the same kind of hardware, except I have an AMD Athlon II X4 processor (64 bit) and a Nvidia graphics card. Same tablet. Same problem. Havent tried the thing with xsetwacom yet. Will do that in a sec and edit this post.

---

### Post by Scayris on 2011-02-11
Hello. So, I'm back... Fed up with the problem I finally followed the procedure described in the tutorial, installing new drivers. Alas, the problem remains.. I also made sure it's not just the computer that's slow, by trying out and concluding that GIMP doesn't have these problems running on Windows, which I have a dual boot set up with... Still, I'd much, MUCH prefer not to use windows, for anything, drawing included, so if there are any other ideas I could try..?

---

### Post by Favux on 2011-02-11
Hi Scayris,

I've been wondering if we could play with a couple of xinput commands for the stylus/eraser.  Enter in a terminal:
```
xinput list
```
to get the "device name" of your Wacom stylus or eraser.  Then enter:
```
xinput list-props "device name"
```
See what's available.  Most likely you'll see the following settings:
```
"Device Accel Constant Deceleration" 1.000000
"Device Accel Adaptive Deceleration" 1.000000
"Device Accel Velocity Scaling" 10.000000
```
Then start modifying them, example:
```
xinput set-prop "Wacom BambooFun 2FG 4x5 Pen stylus" --type=float "Device Accel Constant Deceleration" 1.000000
xinput set-prop "Wacom BambooFun 2FG 4x5 Pen stylus" --type=float "Device Accel Adaptive Deceleration" 1.000000
xinput set-prop "Wacom BambooFun 2FG 4x5 Pen stylus" --type=float "Device Accel Velocity Scaling" 10.000000
```
using your device name in quotes.

You'll probably want to start with/concentrate on "Device Accel Constant Deceleration" with an initial increased value of say 1.250000.  Anyway try varying the values, maybe even decrease them for some.

You'll need to experiment with all of them to which is the best one, or what combination, and what values you need.  If it works the settings won't last through a reboot so you'll need to place them in a start up script.

Let us know if you find something that works.

---

### Post by tordeu on 2011-03-25
I can confirm the lag and I do not use a tablet. This problem is there when using a mouse as well (10.10 x64) and I also experience it with a 11px brush size on a 1280x850 picture.

So, I will highly doubt that an improvement could be achieved by playing around with drivers or settings for the wacom device. jomaksmile mentioned something about a gtk/GIMP problem and that seems more likely. This really feels like the high number of actions/requests generated by using a brush creates the lag. It might be gtk, metacity or something else, but at least it's not a tablet problem.

Let's hope they really have a fix for this. I have not tried this with Natty, yet. I will try so test that, soon. If somebody has also done it, it would be nice to post your experience.

Just some infos about my system: 

[LIST]
[*]Compiz is enabled
[*]using open source drivers on an ATI HD 4350
[*]Q8300 quad core with 3GB of RAM
[*]Ubuntu 10.10 x64
[/LIST]
It might be interesting to know if this is limited to a specific configuration.

---

### Post by 23dornot23d on 2011-03-25
I just had a page open at 5000 x 5000 - (222MBytes) and the lag is there but the pen was quite useable ..... in Gimp v2.7.1 .... obvious lag at 10 x scale but at a normal size of 9 pix size was ok ...... 
( I have compiz running and 3 docks at the moment when I tested it .... AWN - Docky and Cairo-dock - forgot to switch them off - was just trying them out .....)

I have just recently compiled the latest Glib 2.0 and Gtk+3.0 also Babl 0.0.14 and Gegl 0.0.16 ..... would these make a difference or not though .....

I have 2.7.1 running Ubuntu Maverick 10.10 x64 in a /opt/ directory and its reasonably fast .... there is a later version of GIMP 2.7.2 out that I use on a 32bit Ubuntu Maverick from the Matt Walkers repository ..... Matheus PPA ...... ( will get back to you on that as I have to re-boot .....  [COLOR=Red]THIS IS SUPERB - IT really is great for my Pen[/COLOR]

 ..... I use a G-Pen though not a Wacom ......not sure how much difference there is between the drivers for these devices ......

( I also have a usb keyboard plugged in .... usb seperate numeric pad .... and a usb mouse ........ whether more devices would cause problems 
I have noticed with extension USB connectors with 4 more devices added then problems can occur .........)
 
My system has 3 Gig mem Aser Aspire Laptop 7730 zg

[IMG]http://img215.imageshack.us/img215/471/specsp.jpg[/IMG]


Hope this will help it maybe gives you more options ..... just be careful if you go for the PPA ......[COLOR=Red][B] it will overwrite the existing GIMP 2.6.10 ..... and trust me its not real easy to restore it once it has done that ........ 

[/B][/COLOR]These are development versions above 2.6.10/11 ........ 

If you have more than one Ubuntu OS on your system it may be worth checking it out though ..... on one you rarely use ..... or one that you have for testing purposes. Otherwise wait till the New Version is Released ......

If not ..... then try another paint package to get the majority of work done ..... MyPaint is very good ....... and I rarely notice lag in that .......

Best of luck .....

---

### Post by prokoudine on 2011-03-27
> **tordeu said:**
> I can confirm the lag and I do not use a tablet.

Excerpt from a week old IRC log of #gimp channel.

<mitch> Alexia_Death: painting is *much* faster on gtk3
<mitch> i suspect using cairo globally fixed a lot of cairo slowness
<mitch> it's really incredible, zero lag
<mitch> huge brush
<mitch> huge canvas
<mitch> it flickers like hell
<mitch> i could fix that, but then it would be impossible to see another bug fixed
<mitch> first things first
<mitch> i can almost fluently paint with a 1000 px brush on a 5000x5000 image
<mitch> totally fluently with a 500px brush on the same image

So, for really dramatic changes you will have to wait for GTK3 based v3.0. Needless to say, nobody knows yet when it's released.

---

### Post by tordeu on 2011-03-27
@prokoudine:

Thanks for the post. I don't know if I will try gtk3 on 10.10, cause I don't use GIMP that much and 11.04 is only a month away. But I am hopeful for the problem to be fixed then.

---

