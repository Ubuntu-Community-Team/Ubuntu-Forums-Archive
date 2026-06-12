---
title: "root-tail invisibility"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by marx2k on 2006-12-12
I am trying to run root-tail to constantly update a log file on my desktop but unfortunately when I run it, nothing shows up! And the program doesnt give an error.

root-tail -g 800x250+100+50 --color black --shade --minspace --noflicker --frame /var/log/moblock.log,black

Also tried the example given in the man page for root-tail:
root-tail    -g    800x250+100+50   -font   10x20   /var/log/messages,green -font   12x24 /var/log/secure,red,’ALERT’

No dice.

man page says:
Some desktop environments open a virtual root window and make it difficult to share it.  If you  cannot see anything after starting root-tail, try to find a setting "allow programs on desktop" or similar, or manually specify a window id.

How do I tell what the window ID for the desktop is?

---

### Post by marx2k on 2006-12-12
Ok, moving slightly ahead, used xwininfo to find out the ID of my desktop..

```

xwininfo: Window id: 0xe00021 "Desktop"

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1280
  Height: 1024
  Depth: 24
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1280x1024+0+0

```

So when i try:
root-tail --id 0xe00021 --shade  --frame /var/log/moblock.log,black

still nothing shows up

Also tried:
root-tail --id "Desktop" --shade  --frame /var/log/moblock.log,black

Nada.

---

### Post by girishv on 2006-12-12
Do you have read permission of the file(s) you are trying to access ?

Please test it on some file which you can read as a normal user
root-tail --id 0xe00021 --shade --frame /etc/X11/xorg.conf

if it works, then you might have to either change the permission of the file you are trying to root-tail or run it as sudo

Girish

---

### Post by mcduck on 2006-12-12
I'm not sure but I think that Nautilus (that handles the desktop in Gnome) draws wallpaper *above* root window, so you won't ever be able to see the root window itself..

---

### Post by marx2k on 2006-12-12
Grishv: I've also tried as sudo with no luck

Mcduck: I think that is what is happening here, and that's crappy :(
Do you know of another program that does that same job that DOES work? (Don't say gdesklet's tail as that program is amazingly buggy and crashes nicely when trying to tail a 26M file)

---

### Post by mcduck on 2006-12-12
There are some threads in this forum about creating transparent borderless terminals on your desktop so I think that is the way to go.

I believe this might be possible somehow with Conky too.

I'm using borderless transparent Gnome-terminal but I don't think it's possible to do this without Beryl/Compiz.

---

### Post by marx2k on 2006-12-12
I can definately do transparent terminal, but I haven't tried borderless.  The thing about that is I would like it to take up as little memory as possible, and gnome terminal (at least on the laptop) is a 13M footprint.  root-tail has a 220k footprint ;)  I hope there is some way to make this work. It kind of stinks that gnome breaks this functionality.  ](*,) 

Conky does run but I don't think it has a function to tail a file, as far as I know.

---

### Post by mcduck on 2006-12-12
Yeah, I only mentioned Gnome-terminal because I'm using it (for the nice antialiased fonts).

Most people do it with urxvt or eterm which are much lighter, and have built-in support for running without window borders.

here's links to some HowTo's:

[HOWTO: Terminal for desktop background.]("http://www.ubuntuforums.org/showthread.php?t=36811&highlight=desktop+terminal+borderless")
[HOWTO: True or Pseudo-Transparent Borderless Pop-up Terminals]("http://www.ubuntuforums.org/showthread.php?t=81727&highlight=transparent+terminal+howto")

---

### Post by marx2k on 2006-12-12
Well, looks like Conky does exactly what I need plus a lot more. Didn't think it DID have tail, but it definately does :) Allowed me to remove all the desklets I had too. Awesome!

---

### Post by undecidable on 2008-03-05
I know this is old, but got root-tail working so post it just to help anyone else who finds the thread:

1.  Need to set 
		settings > desktop >  behaviour  >  allow progs in desktop window
(this is in Kubuntu, assume there will be something similar in Ubuntu)

2.  Re: marx2k's last point:
  How do I tell what the window ID for the desktop is?
you can run:  xwininfo form a terminal.

However it does not help as all virtual terminals seem to have the same window id.  

3.  One other point worth mentioning:
 if I left the virtual window can came back to it, the root-tail window disappeared.
This can be fixed by adding:
  --reload 5 true

4. I found no way of having it appear on 1 virtual desktop only.  It appears on all virtual desktops.

---

