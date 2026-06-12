---
title: "Assistence iwth gnome-mag (magnifier) command-line parameters"
date: 2007-03-24
forum: Assistive Technology &amp; Accessibility
---

### Post by RKCole on 2007-03-24
Hello, everyone.

I just installed Ubuntu 7.04 today, and I must say that I'm impressed all around.  I'm especially impressed/excited about the changes in gnome-mag (magnifier).  However, I need some assistance with setting up gnome-mag from the command-line.

I currently have a desktop launcher created for the magnifier which starts up the magnifier in a horizontal position on the screen with a zoom factor of 5.0.  The commands/parameters I used in the launcher are as follows:

```

magnifier -hmz 5.0

```

There are two things I need help with (I really hope it's possible) to set up the magnifier a little better for me.

1.  Is there a command-line argument/parameter I can use to remove the cross-hairs?

2.  By default, the magnified portion of the screen is at the bottom of my screen.  Is there something I can do to have this changed so that the top of the screen is the magnified portion?  This would be very helpful to me.

gnome-mag has come a LONG way since I started using Ubuntu in March of 2005 or so.  It is pretty much equivalent to ZoomText.  I really just want to try to configure it as mentioned above, but I now feel I could make a permanent move to Ubuntu as the magnifier is now exactly what I need.

Thanks in advance for any help with this issue.

Take care.

---

### Post by Henrik on 2007-03-29
There seems to be a setting called viewport, but I could not get it to take a value.

Is there any reason why you don't want to run Orca in magnifier-only mode?

Btw, have you tried Beryl? It is now in 7.04 universe and has a fairly good zoom plugin (just need cursor tacking -- working on that).

---

### Post by RKCole on 2007-03-29
Hello, Henrik.

I tried to use the magnifier support in Orca, actually, but (I'm not sure why) it did not work the same way as using the magnifier solely.  For instance, when I tried setting the right and bottom values to maximum and setting top and right to 0 (which was supposed to result in full-screen magnification) full-screen magnification did not work.  I received a completely white/tan screen.  I coudl hear the voice output from Orca, but could not see anything.  I had to actually go into a tty and run
```

killall orca magnifier
orca --disable=magnifier

```
in order to reset things (which was not a big problem).

Also, when I use just the magnifier with the -hmz 5.0 parameters, it works in much the same way as ZoomText does on Windows...but I cannot get this to work in Orca for some reason...It only works when I use the magnifier via command-line options.

I'm not sure what is happening, unless Orca is accessing the older version of the magnifier (I upgraded to v0.14.3 using the --prefix=/usr parameter when running the ./configure file)?  I have Composite enabled in /etc/X11/xorg.conf.  Any ideas on what the issue could be?  I'm using Orca v2.17.1.

I'm not sure how to explain the difference between runnning the magnifier by itself and running it with Orca...If I can I will try to post a screenshot fo each...but I really do not know how to explain the differences.

Also...I downgraded from Ubuntu 7.04...When the newest updates came out for the kernel version 2.6.20-13-generic...my system was inaccessible...so I did a fresh install of Edgy.  I have the magnifier working the same in Edgy as it was in Feisty (and I have the driver for my nVidia card installed)...but I still do not know how to get it to work with Orca.

Thanks for any help you can offer concerning this.

Take care.

---

### Post by RKCole on 2007-03-29
My mistake...I'm using Orca v2.17.92 on Ubuntu 6.10 with latest updates and composite enabled.

---

### Post by RKCole on 2007-03-29
I hope this works.  I'm attaching three screenshots of my desktop.

Desktop1.png:  This is a screenshot of my desktop without any magnification. (As you can see, it's kind of plain and bland...but hey...I'll add an outer space background soon enough.  :) )

Desktop2.png:  This is a screenshot in which the magnifier si running via Orca.  As you can see, all of my icons are pushed down and repositioned in columns...Basically my desktop real-estate shrinks dramatically.  Any windows (like Firefox) that I would open will be pushed down off-screen, so any buttons (like in Orca Preferences) are inaccessible.

Desktop3.png:  This is a screenshot of the magnifier running (solo) via the following settings (Note this is using magnifier v0.14.3):
```

magnifier -hmz 5.0

```

As you can see in the unmagnified portion only the top half of my Desktop is visible, but in the magnified portion you can see the bottom portion.  No windows are decreased in size, and the initial layout fo the desktop is untouched.  the difference is that the magnifier can view all of the window without having to many any arrangements.

I hope this makes sense.

---

### Post by RKCole on 2007-03-31
Henrik.

I installed Beryl on my Edgy system.  It si very amazing.  The only problems I've seen with it are that the title bars of windows I have open (such as the terminal)--which are positioned at the top-left of the screen) are not visible and I cannot move them; the second problem I have noticed is that shortcut keys, such as ALT+F1 no longer work.  It is very amazing, though, and it actually uses less memory than Orca or gnome-mag do.  I look forward to seeing plugins (as you had mentioned) becomign available in teh future.

Thanks for the suggestion on that...For the time being, though, I still would liek to use gnome-mag.

Take care and thanks again. :)

---

### Post by cerdiogenes on 2007-04-22
Hi RKCole,

We disable the composite use in gnome-mag when running through Orca, since we discovered a bug in it. I pretend to make a release of gnome-mag to 2.18.2 to correct this and probably Ubuntu will update this in their repository.

BTW, you are an advanced user and appear very interested in test it, so download the gnome-mag code from SVN (in you command-line type):

svn co [http://svn.gnome.org/svn/gnome-mag/trunk](http://svn.gnome.org/svn/gnome-mag/trunk) gnome-mag

Edit the file magnifier/GNOME_Magnifier.server.in.in and remove the --ignore-composite option. Then enter the gnome-mag folder and type:

./autogen.sh --prefix=/usr
make
sudo make install

Hope this help, and please, post here any problems that you have while running orca/gnome-mag with this full-screen magnification support.

PS.: You need to install the gnome-common package to be able to run the autogen.sh script.

Best regards,
Carlos.

---

### Post by RKCole on 2007-04-23
Hello, cerdiogenes.

I will give this all a try tomorrow.  Although I don't consider myself an advanced Linux user yet, I accept the compliment. :)  I hope to be able to consider myself at an advanced level one day.  Thank you for gnome-mag, as if not for it and the Accessibility Team/Community, I probably would have given up on Linux a long while ago because of my lack of knowledge and experience.  Now, however, I plan to do a complete migration from Windows within the next month. :)  Thank you.

As far as posting any issues/problems here, are there certain files (maybe in the /var directory) ro anything (maybe terminal output) that will be of assistance if any problems arise?  If so, please let me know and I will be sure to monitor any log files or terminal output as best as I can.

Take care.

---

### Post by cerdiogenes on 2007-04-23
I don't know much about Orca, but gnome-mag doesn't generate any file that can represent problems. I only ask it, because this doesn't receive tests. I think that I was the only one who tested it, but only for 3 minutes :-), so it can still have bugs that a more extensive use can give light on them!

Best regards,
Carlos.

---

### Post by RKCole on 2007-04-24
Just compiled the latest SVN version of gnome-mag.  Here si what I've noticed so far:

*The mouse tracking is very smooth.

I've noticed that when the mouse hovers over links which have Tooltips (such as those on the Ubuntu Forums), the magnifier shows the Desktop rather than the Firefox window, although Firefox is open.  Also, any type fo tooltip seems to make the magnifier very "jumpy".

Keyboard tracking (not sure if this is related to Firefox or not):  While typing (here in this posting form, for instance) the magnifier shows only the right-hand portion fo the screen, but not the actual text being typed.

Orca and full-screen:  (NOte that I'm using Orca v2.18.1 as I could nto compile v2.19.1.  How do I go about doing this?)  In Full-screen mode (using Orca) I can see my cursor, but the screen is all black--no windows are shown whatsoever.  HOwever, without Orca running, full-screen magnification works perfectly (just dont know how to get rid of the cross-hairs :) ).

My magnifier setup in Orca:

Positioning:
Top: 0
Left: 0
Right: 1014
Bottom: 400

Screen resolution: 1024x768

Please, let me know whatever you would like me to try and I will do so.  I'm not sure if upgrading to Orca v2.19.1 will make much of a difference (/).  I couldn't compile it on Feisty, though.

I hope that my information is clear and helpful.  Please let me know if it is not and I will try to give better explanations.

Take care.

---

### Post by cerdiogenes on 2007-04-24
Hi RKCole,

> **RKCole said:**
> Just compiled the latest SVN version of gnome-mag.  Here si what I've noticed so far:

*The mouse tracking is very smooth.

I've noticed that when the mouse hovers over links which have Tooltips (such as those on the Ubuntu Forums), the magnifier shows the Desktop rather than the Firefox window, although Firefox is open.  Also, any type fo tooltip seems to make the magnifier very "jumpy".

I don't know how to reproduce this, since when I first started the magnifier with composite the screen get all black and the tooltip appear, but then doesn't go away, leaving trashs in the black screen.

> **RKCole said:**
> Keyboard tracking (not sure if this is related to Firefox or not):  While typing (here in this posting form, for instance) the magnifier shows only the right-hand portion fo the screen, but not the actual text being typed.

Yes, I also saw this here and I think that this is firefox related. Here, while typing I get a grey magnifier screen that I can't reproduce moving the mouse. From what I understand, this appear that firefox is returning a wrong event to orca and orca is calling gnome-mag to magnify a non-visible part of the screen. When I have time I will investigate it with more details.

> **RKCole said:**
> Orca and full-screen:  (NOte that I'm using Orca v2.18.1 as I could nto compile v2.19.1.  How do I go about doing this?)  In Full-screen mode (using Orca) I can see my cursor, but the screen is all black--no windows are shown whatsoever.  HOwever, without Orca running, full-screen magnification works perfectly (just dont know how to get rid of the cross-hairs :) ).

To make the magnifier actually magnify I had to put the string ":0.0" (without the ") in the "Source display:" field. I actually think that this can be a gnome-mag bug, but I will have to investigate it a little more.

> **RKCole said:**
> My magnifier setup in Orca:

Positioning:
Top: 0
Left: 0
Right: 1014
Bottom: 400

Screen resolution: 1024x768

Please, let me know whatever you would like me to try and I will do so.  I'm not sure if upgrading to Orca v2.19.1 will make much of a difference (/).  I couldn't compile it on Feisty, though.

I hope that my information is clear and helpful.  Please let me know if it is not and I will try to give better explanations.

Take care.

I hope my answer help you get this working.

Best regards,
Carlos.

---

### Post by Cabb on 2007-04-24
I just upgraded Ubuntu as well, and Orca and gnome-mag for that matter too. I haven't managed to get gnome-mag to work properly though. I just get an almost black screen where I can see a little bit at the top and sometimes some lines all over the place when I move the mouse :)
I'll keep trying, this is getting better and better!
Meanwhile I'd just like to mention how impressed I am with Orca. The new eSpeak is veeery responsive for me.
I now surf the web with the latest development release of Firefox, plus Orca, and that's where I am posting from!

This is truly great!

/Daniel
(let's see if I manage to get this post up now...)

---

### Post by cerdiogenes on 2007-04-24
Hi Cabb,

Probably you don't saw in my last post the information to put the string ":0.0" in the "Source display:" field in orca magnifier preferences.

After this the magnifier worked for me.

Best regards,
Carlos.

---

### Post by RKCole on 2007-04-24
Adding :0.0 solved my problem.  Now I can add a bit more to my experiences with full-screen using Orca.

Keyboard tracking:  I just discovered something about keyboard tracking.  It seems like, while I'm typing this, it appears like keyboard tracking begins at the very right-hand border fo the text form for posting.  Each time I type a keystroke, I see the magnifier kind of jump, as if following my key input, but it keeps going further to the right until it is off-screen, thus giving a completely gray screen.  It also does nto seem that the tracking si reset after the ENTER key is hit, and a new line is created.  I hope that I explained this clearly enough.

NOw, under full-screen magnification, I do not have the problem with tooltips causing my screen to go black.  It seems to only happen when I have it set up for split-screen.  But...I dod not have the :0.0 entered in the Source text field previously.  Yes, this problem does not occur now with the :0.0 inserted.

---

### Post by linbetwin on 2007-04-27
Yes, the magnifier starts tracking the cursor only when it reaches the end of the magnification screen. It would be much better if the focus kept the cursor in the middle of the screen when typing or pressing ENTER. It used to do that in previous versions of gnome-mag.

---

### Post by cerdiogenes on 2007-04-30
Hi linbetwin,

> **linbetwin said:**
> Yes, the magnifier starts tracking the cursor only when it reaches the end of the magnification screen. It would be much better if the focus kept the cursor in the middle of the screen when typing or pressing ENTER. It used to do that in previous versions of gnome-mag.

The default software that control the cursor tracking of gnome-mag in GNOME, consequently in Ubuntu, is Orca. Probably your comment is about gnopernicus IIRC.

In the Orca page, [http://live.gnome.org/Orca#head-703c4a04c033e24196fb536415071406a015bc17](http://live.gnome.org/Orca#head-703c4a04c033e24196fb536415071406a015bc17), you have informations about how to contact the developers and ask for this implementation.

Best regards,
Carlos.

---

### Post by RKCole on 2007-05-19
The main issue that I see right now, unfortunately, is that the magnifier uses between 83%-100% of my CPU time; I use a Pentium 4 2.80GHz processor.  I do not know if it is something I have set up incorrectly or not, though.

Were there any new SVN releases since my last post?  I was away on a much needed vacation, and so I am trying to "catch up".

Take care.

---

### Post by RKCole on 2007-05-20
I decided to try to download the latest revision of gnome-mag (Revision 502) via SVN.  I tried to compile it via the following:

```

sudo ./autogen.sh --prefix-/usr
sudo make
sudo make install

```

gnome-mag no longer works, and I do not have an older revision.  How can I fix this?

Thanks for any advice.

Take care.

---

### Post by RKCole on 2007-05-20
Well, I ran the following:

```

sudo apt-get remove gnome-mag
sudo apt-get install gnome-mag

```

I ran it on a hunch as I figured it would probably install the latest version of gnome-mag that comes with Feisty.  Needless to say, my hunch was correct. :)  I had to temporarily use Windows for the past day...but I'm back home with Ubuntu now! :))  I'm glad to be home. (haha)

Take care.

---

### Post by cerdiogenes on 2007-05-25
Hi RKCole,

I released a new version of gnome-mag (0.14.4) that I think that will be packed for Ubuntu 7.04 in the next days.

This is the announcement: [http://mail.gnome.org/archives/gnome-accessibility-list/2007-May/msg00012.html](http://mail.gnome.org/archives/gnome-accessibility-list/2007-May/msg00012.html)

Here is where you can download the tarball: [http://download.gnome.org/sources/gnome-mag/0.14/gnome-mag-0.14.4.tar.gz](http://download.gnome.org/sources/gnome-mag/0.14/gnome-mag-0.14.4.tar.gz)

This correct the workaround of setting the source display string in Orca to :0.0, but this still show the pointer in full-screen mode.

Best regards,
Carlos.

---

### Post by RKCole on 2007-06-02
Hello, cerdiogenes.

Thanks for the information.  I now have the latest version installed, and it works great.

There si one thing I am kind fo curious about, but I am not sure if it is somethign dealing with gnome-mag or just Ubuntu in general.

Basically, after soem time of using gnome-mag (activating/deactivating), my bottom panel disappears when I move my mouse pointer over it.  The only thing which I have foudn to solve this, so far, si to hit CTRL+ALT+F2 to enter a command-line terminal and type:

```

sudo /etc/init.d/gdm restart

```

This works, but I have to ensure that any applications I am running (i.e. OpenOffice) are closed as when GDM restarts, everything is killed.

As I said, though, I don't know if this si a Ubuntu/GNOME issue ro somethign to do with gnome-mag.

Any ideas?

Thanks.

Take care.

---

### Post by cerdiogenes on 2007-06-05
Hi RKCole,

I need more informations to try to realize what is happening in your computer.

> **RKCole said:**
> Hello, cerdiogenes.

Thanks for the information.  I now have the latest version installed, and it works great.

There si one thing I am kind fo curious about, but I am not sure if it is somethign dealing with gnome-mag or just Ubuntu in general.

Basically, after soem time of using gnome-mag (activating/deactivating), my bottom panel disappears when I move my mouse pointer over it.  The only thing which I have foudn to solve this, so far, si to hit CTRL+ALT+F2 to enter a command-line terminal and type:

Can you give informations of how much is this sometime, how frequently you active/deactive gnome-mag and what is the process that you take to do this activation/deactivation? I try to reproduce it here without success.

Could you inform your computer configuration?

In the past, GNOME panels lost a property when composite where used (the windows could overlay they), maybe this can be some similar problem, but it's very difficult to track if I can't reproduce it here.

Best regards,
Carlos.

---

### Post by RKCole on 2007-06-27
I apologize, but it seems to just happen randomly.  I do not think it is related to gnome-mag now, though.

---

### Post by cheesphht on 2008-10-29
> **RKCole said:**
> Hello, cerdiogenes.

I will give this all a try tomorrow.  Although I don't consider myself an advanced Linux user yet, I accept the compliment. :)  I hope to be able to consider myself at an advanced level one day.  Thank you for gnome-mag, as if not for it and the Accessibility Team/Community, I probably would have given up on Linux a long while ago because of my lack of knowledge and experience.  Now, however, I plan to do a complete migration from Windows within the next month. :)  Thank you.

As far as posting any issues/problems here, are there certain files (maybe in the /var directory) ro anything (maybe terminal output) that will be of assistance if any problems arise?  If so, please let me know and I will be sure to monitor any log files or terminal output as best as I can.

Take care.

Hey, 

I was wondering - did you ever get this to work?  I'm new to Ubuntu and can follow that a little but . . . I really don't even know what "full screen mode" or - I forget the name of it now - means! I don't want it to, of course, magnify the whole screen (if it indeed means what it says which there is a lot of doubt today if anything really means what it says) 

In windows I had a nice user adjustable box that I could virtually put anywhere I wanted and it would follow the mouse or the caret when I was typing. Is there anything like that in this Ubuntu?

Hope someone sees this.

---

### Post by RKCole on 2008-10-29
Hello, cheesphht.

I never did come up with the solution to this situation via the command-line.  In Ubuntu 8.04, however, you can set everything you need through the Magnifier tab in Orca Preferences--if you are not familiar with Orca, it is a magnifier/screen reader.  You can access it by doing the following:

[LIST=1]
[*]Press ALT+F2 to open the **Run Application** dialog box.
[*]When the dialog box opens, type in 
```
orca
```
and press ENTER.
[/LIST]

Orca will start and will read off options for you to select from by keyboard input.

In any case, there is a preferences button on the Orca application window which has a tab dedicated to the magnifier.  I just tested this on my system, and it allows to dock the magnifier on the top of the screen.

Full-screen magnification refers to zooming in on the entire screen area.  I used to dislike this until I began using Compiz Fusion with its eZoom plug-in.  Compiz Fusion is a grahipcs accelerated window manager which has a lot fo features to it.

In any case, if I can be of any help to you, please e-mail me.  I will be gone all day tomorrow, but I can write back tomorrow evening.

Please take care, and have a great day.

---

