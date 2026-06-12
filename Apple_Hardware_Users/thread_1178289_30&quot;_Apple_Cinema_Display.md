---
title: "30&quot; Apple Cinema Display"
date: 2009-06-04
forum: Apple Hardware Users
---

### Post by rfindler on 2009-06-04
Hi all:

I'm having trouble getting my apple cinema display to use its proper resolution of 2560x1600. Instead, it seems stuck on 1280x800. I tried to xrandr to fix this, but I got stuck (as below). Any help would be appreciated!

The problem seems to come when I try to use --add-mode to say that my monitor is 2560x1600, but I included more of the transcript in case there is something useful there that I'm missing.

tia,
Robby

robby@taitung:~$ xrandr --fb 4480x1600
robby@taitung:~$ xrandr
Screen 0: minimum 320 x 200, current 4480 x 1600, maximum 4480 x 1600
VGA1 disconnected
DVI0 connected 1920x1200+0+0 495mm x 310mm
   1920x1200      59.9*+   60.0  
VGA2 disconnected
DVI1 connected 1280x800+1920+0 641mm x 401mm
   1280x800       59.9* 
robby@taitung:~$ xrandr --newmode 2560x1600 348.50 2560 2760 3032 3504 1600 1603 1609 1658 -hsync +vsync
robby@taitung:~$ xrandr --addmode DVI1 2560x1600
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  18 ()
  Serial number of failed request:  27
  Current serial number in output stream:  28
robby@taitung:~$ xrandr --output DVI1 --mode 2560x1600
xrandr: cannot find mode 2560x1600
robby@taitung:~$ xrandr
Screen 0: minimum 320 x 200, current 4480 x 1600, maximum 4480 x 1600
VGA1 disconnected
DVI0 connected 1920x1200+0+0 495mm x 310mm
   1920x1200      59.9*+   60.0  
VGA2 disconnected
DVI1 connected 1280x800+1920+0 641mm x 401mm
   1280x800       59.9* 
  2560x1600 (0x11f)  348.5MHz
        h: width  2560 start 2760 end 3032 total 3504 skew    0 clock   99.5KHz
        v: height 1600 start 1603 end 1609 total 1658           clock   60.0Hz
robby@taitung:~$

---

### Post by rfindler on 2009-06-04
Turns out what was missing was this line in my xorg.conf:

  Option "AllowDualLinkModes"
[COLOR=#888888]
in the Device section.

Thanks to [/COLOR]Maarten Maathuis, who also leaves this word of warning:

On Thu, Jun 4, 2009 at 10:10 AM, Maarten Maathuis <[EMAIL="madman2003@gmail.com"]madman2003@gmail.com[/EMAIL]> wrote:
> xf86-video-nv which i guess you're using doesn't unconditionally
> support dual link dvi. Some bios'es don't init it appearantly.
>
> There is an option to force it, but you could end up with a blank screen.
>
> Option "AllowDualLinkModes"
>
> Maarten.
>

---

### Post by DomesDKG on 2011-04-26
> **rfindler said:**
> Turns out what was missing was this line in my xorg.conf:

  Option "AllowDualLinkModes"
[COLOR=#888888]
in the Device section.

Thanks to [/COLOR]Maarten Maathuis, who also leaves this word of warning:

On Thu, Jun 4, 2009 at 10:10 AM, Maarten Maathuis <[EMAIL="madman2003@gmail.com"]madman2003@gmail.com[/EMAIL]> wrote:
> xf86-video-nv which i guess you're using doesn't unconditionally
> support dual link dvi. Some bios'es don't init it appearantly.
>
> There is an option to force it, but you could end up with a blank screen.
>
> Option "AllowDualLinkModes"
>
> Maarten.
>

I added Option "AllowDualLinkModes" to my Xorg.Conf, but the options for the higher resolutions aren't showing up.  I know it's just the settings though - the resolutions work fine under windows on the same machine.  Any ideas what else I need to add?

P.S. I put it in the Monitor Section, was that appropriate?

---

### Post by nfmangano on 2013-04-04
Bump, I have this problem as well. The suggested solutions didn't in my case either.

---

