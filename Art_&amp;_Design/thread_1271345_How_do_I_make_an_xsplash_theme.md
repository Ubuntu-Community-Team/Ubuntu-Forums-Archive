---
title: "How do I make an xsplash theme?"
date: 2009-09-20
forum: Art &amp; Design
---

### Post by TheForkOfJustice on 2009-09-20
I would like to know how to make an xsplash theme.  Can someone please help?

---

### Post by LiquidMeson on 2009-09-20
I actually just started playing with it today :D. You can find the xsplash images in /usr/share/images/xsplash. By changing those images you can modify the xsplash. Thats probably just the basics tho, i'm sure theres a way to get to the more nitty gritty. Just not sure where the files are. You can also test it out when your done editing by running "sudo xsplash" in the terminal, followed by ctrl-c to close it.

---

### Post by TheForkOfJustice on 2009-09-21
At least that part is easy.

Do you know how to change the default theme?

How about changing the special animations they have?

---

### Post by LiquidMeson on 2009-09-22
So I was digging around alittle and I found this application called [reconstructor]("http://www.reconstructor.org/"). Maybe that will help? I've never tried it so i'm just shooting in the dark. I wasn't sure if you meant change the default theme as in just changing it,.. or changing it on the whole install cd. Also not sure what you mean about special animations. If your looking to just change your theme for your ubuntu desktop download say a meta-city package off of gnome-look.org (which seemes to be off-line right now?/ or the equivalent website) and drag and drop the package into the theme chooser (right click/change background/theme)

---

### Post by TheForkOfJustice on 2009-09-22
> **LiquidMeson said:**
> So I was digging around alittle and I found this application called [reconstructor]("http://www.reconstructor.org/"). Maybe that will help? I've never tried it so i'm just shooting in the dark. 

I know about reconstructor. It's not what I'm looking for.

> I wasn't sure if you meant change the default theme as in just changing it,.. or changing it on the whole install cd.

Both, really.  I looked through both the **xsplash** and **xsplash-ubuntu-artwork** deb files and didn't see a theme index file, conf file or postinst script that will define how it behaves.  I can't find much documentation on xsplash at all.  

I also need to know if I can install more than one theme at once and switch between the two on the fly or is it only one theme at a time.  Mostly for testing purposes.

> Also not sure what you mean about special animations.

Throbbers, basically, although they don't really seem to show a specific progress...

The current xsplash theme has a bar that shines a light in one direction: 

[http://www.youtube.com/watch?v=cOJUY35N-pU]("http://www.youtube.com/watch?v=cOJUY35N-pU")

Another exists which looks like an atom nucleus (or something...):

[http://www.youtube.com/watch?v=StNanFooAu8]("http://www.youtube.com/watch?v=StNanFooAu8")

And there are many other examples in YouTube if you do a search for xsplash.

I wish to know how to make those kinds of animations for my own xsplash theme.

>  If your looking to just change your theme for your ubuntu desktop download say a meta-city package off of gnome-look.org (which seemes to be off-line right now?/ or the equivalent website) and drag and drop the package into the theme chooser (right click/change background/theme)

I'm not looking for a new desktop theme.  
Gnome-Look.org wouldn't have xsplash themes anyway.
I'm looking for instructions on how to make an advanced xsplash theme.

---

### Post by MadsRH on 2009-09-23
Hi
I created the "atom nuclear" version you mentioned above. You'll need a multiframe .png image. There's a bit more details and link in my blogpost: [http://anotherubuntu.blogspot.com/2009/09/karmic-status-and-artwork-update.html](http://anotherubuntu.blogspot.com/2009/09/karmic-status-and-artwork-update.html)

---

### Post by TheForkOfJustice on 2009-09-24
> **MadsRH said:**
> Hi
I created the "atom nuclear" version you mentioned above. You'll need a multiframe .png image. There's a bit more details and link in my blogpost: [http://anotherubuntu.blogspot.com/2009/09/karmic-status-and-artwork-update.html](http://anotherubuntu.blogspot.com/2009/09/karmic-status-and-artwork-update.html)

Ugh...how do you make it so they animate so smoothly?  I'm certain you didn't draw each frame by hand.

Also, are their specifications on how big the throbber frames are supposed to be?  Any other specs I should know?

---

### Post by LiquidMeson on 2009-09-25
[http://ubuntuforums.org/showthread.php?p=7886454](http://ubuntuforums.org/showthread.php?p=7886454)
[http://ubuntuforums.org/showthread.php?t=1236727&page=18](http://ubuntuforums.org/showthread.php?t=1236727&page=18)

keep in mind xsplash is just emerging. I suppose you could check out the ppa's or play with the /etc/gdm/Init/Default to get your xsplash permanent ie. adding -f 124 and changing your animation png. Would be interesting to know if madsrh did the images from scratch. o_O

---

### Post by TheForkOfJustice on 2009-09-26
> **LiquidMeson said:**
> [http://ubuntuforums.org/showthread.php?p=7886454](http://ubuntuforums.org/showthread.php?p=7886454)
[http://ubuntuforums.org/showthread.php?t=1236727&page=18](http://ubuntuforums.org/showthread.php?t=1236727&page=18)

keep in mind xsplash is just emerging. I suppose you could check out the ppa's or play with the /etc/gdm/Init/Default to get your xsplash permanent ie. adding -f 124 and changing your animation png. Would be interesting to know if madsrh did the images from scratch. o_O

Yes it would be interesting if he did those animations by scratch but there is no way in Hell someone would.  The fiery letters one is especially interesting. If we beg enough maybe he'll let us in one  it with great detail. 

It's the animations more than anything that I'm interested in.  Would love to be pointed towards a tutorial.  I just need to make one according to xsplash's specs after I get a good resource.

And what does "-f 124" do and where do I put it?

---

### Post by cro on 2009-10-11
> **TheForkOfJustice said:**
> And what does "-f 124" do and where do I put it?

OK, figured this one out.

Using MadsRH's fiery animation file ([http://dl.getdropbox.com/u/175241/boot/x-splash.png](http://dl.getdropbox.com/u/175241/boot/x-splash.png)), I downloaded the PNG to a folder, then copied it to
```
/usr/share/images/xsplash/throbber_fiery.png
```
This animation has 60 frames, so the command that runs xsplash on boot needs to be modified.

The file /etc/gdm/Init/Default contains the following:
```

if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --gdm-session --daemon
fi
```

To update your loading animations, simply modify the launch command as follows
```

if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --gdm-session --daemon -t throbber_fiery.png -f 50
fi
```
This tells xsplash to use a new animation source PNG, and tells xsplash how many frames are in the file.

You can use the other options to manually override the other elements (background, logo) for your xsplash.

I've not experimented further yet.

---

### Post by TheForkOfJustice on 2009-10-15
Hmm.  I'll have to investigate further it seems.  If I have to edit the file personally to change the xsplash theme, than it may be unlikely that xsplash will be themeable like metacity. Maybe.  Would be a better story if it used gconf.

You may be stuck with a single xsplash theme unless you manually edit a lot of files and that will take a lot of study on how xsplash works.  Guess I'll have to start learning about the program's files first before I start my theme-making.

---

### Post by Ademan on 2009-10-22
I too am curious about this.  I'd rather not modify /etc/gdm/Init/Default directly, instead I'd rather find out what calls it, and conditionally use /etc/gdm/Init/Themed which might look up theme information from somewhere (gconf if you so wish).

For the moment here's the relevant portion of my /etc/gdm/Init/Themed

```
if [ -x '/usr/bin/xsplash' ];
then
    if [ "$BACKGROUND_IMAGE" ]; then
        bg="--background $BACKGROUND_IMAGE"
    fi

    if [ "$LOGO_IMAGE" ]; then
        logo="--logo $LOGO_IMAGE"
    fi
    if [ "$THROBBER_IMAGE" ]; then
        throbber="--throbber $THROBBER_IMAGE"
    fi
    if [ "$FRAME_COUNT" ]; then
        frame_count="--frames $FRAME_COUNT"
    fi
    if [ "$PING_PONG" ]; then
        pingpong="--pingpong"
    fi

        /usr/bin/xsplash --gdm-session --daemon $bg $logo $throbber $frame_count $pingpong
fi
```

My idea for the moment, is to have whatever calls /etc/gdm/Init/Default to call this instead with the environment variables set to control the theme.  These values could be extracted from gconf or a text file (hell or an rc file that could serve as the theme).

Also note I haven't tested that at all, but I'm relatively confident in my sh-fu and I'll test it in a short while, I just wanted to dump my thoughts somewhere.

cheers,
Dan

EDIT: also here are the args for xsplash, if you didn't infer them from my script:

```

--gdm-session, -g       Run in gdm session
--background, -b        Filename for background image
--daemon, -d            Run in daemon mode
--logo, -l              Filename for logo image
--throbber, -t          Filename for throbber image
--frames, -f            Number of frames for the throbber (default 50)
--pingpong, -p          Whether to reverse throbber directions
--timeout, -x           Timeout (in seconds - 15s by default)
--add-signal, -s        Add a signal to listen for.

```

I ripped these straight from the source code, as xsplash --help would error before it printed the help.

---

### Post by pinguino_ on 2009-11-12
*> I ripped these straight from the source code, as xsplash --help would error before it printed the help.*

To get the help as a regular user, enter the following in a terminal window:

```
sudo -u gdm xsplash --help
```

---

