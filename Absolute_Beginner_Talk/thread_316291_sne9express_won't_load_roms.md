---
title: "sne9express won't load roms"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by Famicommie on 2006-12-10
Running Edgy Eft 64-bit

Today I found my old USB gamepad and thought I'd try it out on some ROMS. At one point I had heard good things about a program called snes9express so I thought I'd try it out. So far it's been a disaster.

The first thing I noticed was that the gamepad didn't work. A quick search on the forums showed me how to get my gamepad running.

Next, I noticed that I had no sound. I messed with some of the options, but couldn't get anything. Anyone have any idea why that might be? Using a Creative Audigy 2 with the ALSA drivers.

While I was trying to find a solution to the sound problem, I opened up the snes9express preferences console and completely broke the application >.< First I pointed to the correct directory where I had stored the single ROM I d/led. While under the "Paths" tab is where I made what seems to be the biggest mistake. I changed the snes9x directory. Now nothing works. I tried doing a search for the proper directory using the terminal and using the GUI to no avail. This is the error message:

```
/usr/share/osnes9x "/home/fami/roms/Chrono Trigger (U).smc"
execvp("/usr/share/osnes9x", ...):
No such file or directory

- could not execute /usr/share/osnes9x
- make sure you have the correct snes9x path
  set in Preferences / Paths.


```

This problem comes to me a lot in Linux. First I tried installing nethack, but I couldn't find the folder where the ASCII version was kept, let alone the config.nh file.

What can I do to get snes9express to begin working properly? What can I do to get sound?

---

### Post by mcduck on 2006-12-10
Let's see.. For the first thing, remove everything from the snes9x path in settings. You shouldn't need to have anything there. If the fields is empty snes9express automatically trys to find the snes9x executable from directories in your $PATH (and that should work just fine).

About sound, well, I don't know. I have enabled 'sound', 'stereo', filters', 'thread sound', 'interpolate', 'envelope' and 'sync' and adjusted 'rate' to 44000Hz. Works fine for me.

---

### Post by Famicommie on 2006-12-10
Thanks mcduck. That got it to where I was before, wherein it'll load up the title screens and stuff, but I still don't get sound and I still can't play anything.

For instance on Chrono Trigger (btw, this is totally legal and legit, I own these games but all of my systems are boxed up from moving) I get the swinging pendulum leading to the actual title, and then the window goes black. In Megaman X 3 the Capcom logo will flash, but once again the window goes black.

I'd really like to play these games. Any ideas on why the ROM is stopping before it gets to any gameplay sequences, or why I still can't get sound?

(like I said: Creative Audigy 2 with ALSA and I'm using a Radeon X800 Pro with the proprietary ATI drivers)

---

### Post by FredSambo on 2006-12-10
i have better luck with ZSNES, and i believe you can get it using apt-get.

---

### Post by Famicommie on 2006-12-11
> **FredSambo said:**
> i have better luck with ZSNES, and i believe you can get it using apt-get.

I appreciate the suggestion, but I believe that the best way to learn new things is to stick with the various aspects until the user knows enough about them to make it work.

I get the titular screens when I have the video preferences set to have the power button run X11snes. When I tried changing it to openGL I got the following error message:

```
osnes9x "/home/fami/roms/Mega Man X 3 (US).smc"
execvp("osnes9x", ...):
No such file or directory
- could not execute osnes9x
- make sure you have the correct snes9x path
  set in Preferences / Paths.

```

Also, still no sound :(

---

### Post by po0f on 2006-12-11
Famicommie,

Don't take FredSambo's suggestion for granted, he may have used both programs and is suggesting (from his experience) which emulator he likes best.  I can also vouch for zsnes.  :)

As for sound issues, this fixes it for zsnes:
```
[FONT="Courier New"]$ cat ~/.asoundrc
pcm.!default {
	type hw
	card 0
}

ctl.!default {
	type hw
	card 0
}
[/FONT]
```

---

### Post by mcduck on 2006-12-11
zsnes never worked for me..

About using OpenGL output with snes9x, are you sure you have installed 'snes9x-opengl'..

---

### Post by Famicommie on 2006-12-11
> **po0f]Don't take FredSambo's suggestion for granted, he may have used both programs and is suggesting (from his experience) which emulator he likes best. I can also vouch for zsnes.:) [/quote]

And I certainly plan on trying out zsnes, but this current predicament seemed like an excellent opportunity for me to start honing my Linux skills. Also, I like the fact that snes9x is coded in assembly.

[QUOTE=mcduck said:**
> zsnes never worked for me..

About using OpenGL output with snes9x, are you sure you have installed 'snes9x-opengl'..

In fact, I *hadn't* installed snex9x-opengl! I had no idea that it didn't come with the package from the add/remove programs menu. So, I fired up Synaptic and there it was. And the best part about it is that all of a sudden I had sound!

The initial glee wore off, though, when the ROM commenced to freeze again as soon as the intro screen finished. Black window, stuck note coming from the sound output. The sound even continued to play after I had closed the window and snes9x, but I was able to silence it by killing the process from the terminal. This was what snes9x told me after I killed its process:

```
osnes9x "/home/fami/roms/Chrono Trigger (U).smc"
joystick: No joystick found.
Can't open "/dev/mem", full screen mode not available: Permission denied
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

osnes9x terminated by signal 15 "Terminated"
```

I know why it didn't find the joystick (in my haste to see if the ROM would work I didn't change the input from /dev/js0 to /dev/input/js0) but I'm not sure what it wants with me changing the permissions or what is expected insofar as the Xlib.

Please guys, I appreciate all the help and I'm almost there!

---

### Post by po0f on 2006-12-12
Famicommie,

[quote=Famicommie]Also, I like the fact that snes9x is coded in assembly.[/quote]
The important parts of zsnes are coded is ASM as well.  ;)

Do you have direct rendering enabled?  Post the output of this command (run it from a terminal):
```
[FONT="Courier New"]$ glxinfo | grep direct[/FONT]
```

---

### Post by Famicommie on 2006-12-12
Thank you for coming back to help me po0f!

Hoo boy, things have changed. Due to some other reasons, I recently reinstalled Ubuntu and changed from 6.10 64bit to 6.06 32bit. Reinstalled and copied everything I wanted back onto the HD, and tried to fire up snes9express again.

Running under X11, it seems to work just fine but still won't give me sound. Trying to run under OpenGL, however, is a different story. (Keep in mind that using OpenGL was what gave me sound before). The error code I get is as follows:

> osnes9x "/home/fami/ROMS/Chrono Trigger (U).smc"
joystick: No joystick found.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  26
  Current serial number in output stream:  28
Rate: 22050, Buffer size: 2048, 16-bit: yes, Stereo: yes, Encoded: no
Found ROM file header (and ignored it).
"CHRONO TRIGGER" [checksum ok] HiROM, 32Mbits, Type: ROM+RAM+BAT, Mode: 21, TV: NTSC, S-RAM: 8KB, ROMId: ACTE Company: C3 CRC32: 2D206BF7

osnes9x returned error code 1

I ran your command to see what was up, and I was informed that direct rendering is enabled. A google search on "osnes9x returned error code 1" gave me no results in English.

I might just wind up trying out zsnes in the morning, but I sure would like to know what snes9expresses problems are with my system.

Thanks for all of the help so far you guys.

---

### Post by tyran on 2007-11-21
Use:

sudo ln -s /usr/bin/snes9x /usr/bin/osnes9x


Thats all.

---

