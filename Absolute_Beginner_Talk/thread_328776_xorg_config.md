---
title: "xorg config"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Lowfront on 2006-12-31
alright I'm trying to get compiz going and I need to configure xorgconfig file or whatever....



so I did this

sudo dpkg-reconfigure xserver-xorg



but I realy don't think that was right because It started asking me all these questions.  I was answering them thinking it was just a few things then I would be able to edit the file.  But there were questions that I think could seriously mess up the computer if I answered wrong.  Which I know I did.  So now what?  I just closed the window when I realized it wasn't what I was sopposed to be doing.


So anyways how do I configure the xconfig file.








. Configure XorgEdit your Screen section and modify your DefaultDepth

    DefaultDepth 24

Warning this options are necessary !

first activate dri,dbe, glx and all necessary modules like this :

    Section “Module”

    # Load “GLcore”

    Load “bitmap”

    Load “ddc”

    Load “dbe”

    Load “dri”

    Load “extmod”

    Load “freetype”

    Load “glx”

    Load “int10&#8243;

    Load “type1&#8243;

    Load “vbe”

    EndSection

and remove all other option in device section like this :

    Section “Device”

    Identifier “Intel Corporation Intel Default Card”

    Driver “i810&#8243;

    BusID “PCI:0:2:0&#8243;

    Option “XAANoOffscreenPixmaps”

    EndSection

and you must have:

    Section “Extensions”

    Option “Composite” “Enable”

    EndSection

---

### Post by d3v1ant_0n3 on 2006-12-31
In terminal, run ```
sudo gedit /etc/X11/xorg.conf
```

Note, the capital X is important (Linux is case sensitive).

Then edit the file to your heart's content.

---

### Post by _simon_ on 2006-12-31
If you mess up and find you can no longer login afterwards then make note of this:

```

sudo nano /etc/X11/xorg.conf

```

So that you can edit your Xorg from the command prompt.

---

### Post by Lowfront on 2006-12-31
well I officall did mess everything up...

Its funny too I just downloaded acronis yesterday and made a back up.

Thankfuly



alright so now I'm back to square one

Could someone please go through the few things I have to do with xorg and help me out

I'm looking at 

[http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/)

[COLOR="DarkOrange"]
WHAT DO THEY MEAN BY THIS??????[/COLOR]

first activate dri,dbe, glx and all necessary modules like this :

    Section &#8220;Module&#8221;

  [COLOR="Red"] # Load &#8220;GLcore&#8221;[/COLOR]

    Load &#8220;bitmap&#8221;

    Load &#8220;ddc&#8221;

    Load &#8220;dbe&#8221;

    Load &#8220;dri&#8221;

    Load &#8220;extmod&#8221;

    Load &#8220;freetype&#8221;

    Load &#8220;glx&#8221;

    Load &#8220;int10&#8243;

    Load &#8220;type1&#8243;

    Load &#8220;vbe&#8221;

    EndSection



and remove all other option in device section like this :

    Section &#8220;Device&#8221;

    Identifier &#8220;Intel Corporation Intel Default Card&#8221;

    Driver &#8220;i810&#8243;

    BusID &#8220;PCI:0:2:0&#8243;

    [COLOR="Red"]Option &#8220;XAANoOffscreenPixmaps&#8221;[/COLOR]

    EndSection



and you must have:
[COLOR="Red"]
    Section &#8220;Extensions&#8221;

    Option &#8220;Composite&#8221; &#8220;Enable&#8221;

    EndSection[/COLOR]

is required.

and restart gdm

---

### Post by Lowfront on 2006-12-31
So I add this even with the # symbol?

 # Load “GLcore”


delete this

Option “XAANoOffscreenPixmaps”





and add this at the end?


Section “Extensions”

Option “Composite” “Enable”

EndSection

---

