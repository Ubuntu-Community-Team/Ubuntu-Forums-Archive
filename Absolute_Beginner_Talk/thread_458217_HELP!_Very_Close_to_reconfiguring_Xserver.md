---
title: "HELP! Very Close to reconfiguring Xserver"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-05-29
Hi,
I posted earlier about my system crashing while trying to reconfigure my ATI X1650. (See 'Expanding Screen Resolution').

Now I've FINALLY gotten the reconfiguration interface to come up - I'm STILL in recovery mode, but SOMETHING I'm entering is wrong, because when I finish and try to do: 'dpkg-reconfigure gdm', it says 'Load failed' Here is the most I can remember of what I'm entering during the reconfiguring:

- all settings as default on keyboard (no autodetection - I enter us)
X Server Driver: ati
PCI Bus port: PCI 2:0:0
Memory borrowed: 0
Use Kernel Framebuffer: yes
Mouse port: /dev/input/mice
Mouse Protocal: ImPS/2
Emulate 3 button mouse: yes
X.Org Server Modules - Interface says that the default is to enable ALL of these:
  bitmap
  dbe
  ddc
  dri
  extmod
  freetype
  glx
  int10
  record
  v41
  vbe
(So I enabled all)

Monitor Autodetection: Yes
Horizaontal freq. rate 24-82
Vert Refresh rate: 48-76


That's the most I can remember. If ANYONE can help me see what I'm doing wrong, I'd really appreciate it. Many Thanks, Frank

---

### Post by arochester on 2007-05-29
I don't recognise:> dpkg-reconfigure gdm You're not reconfiguring your Gnome Desktop, you're reconfiguring your xserver. Try this command:> sudo dpkg-reconfigure xserver-xorg


---

### Post by Brightbelt on 2007-05-29
I''m sorry if I wasn't clear...I'm already doing that command you just stated to BRING UP the reconfiguration process in the first place. So that part is not a problem.

I'm doing the command 'sudo dpkg-reconfigure gdm'  AFTER I've completed doing the reconfiguring interface in order to reload my desktop. 

I got these procedures from this forum thru a google search. And I do trust these instructions; they've come closer to working than any other help I've received.

Many Thanks for helping and I need more if you can, Frank Bright

---

### Post by arochester on 2007-05-29
When you reconfigure your xserver you should just need to > sudo reboot and the graphical interface should come up. Where > sudo dpkg-reconfigure gdm comes in I don't know... If your graphical interface does not come up then reconfigure your xserver again, but specify VESA and not ATI. You might have to restart specific drivers later.

---

### Post by Brightbelt on 2007-05-29
Thanks about the Vesa setting!! I think that made the difference, because I rebooted and my screen resolution choices are higher now as a result, which is what I was trying to get in the first place.

My sense is that since this is working and my resolutions are where  I want them now, I should fool with drivers unless I'm prompted by the computer to do so. Am I correct?

Again, Many, Many Thanks!!!  This took a while, Frank Bright

---

### Post by Brightbelt on 2007-05-29
That is 'should NOT fool with drivers unless the computer prompts me to do so'.

Also I did leave out the 'dpkg-reconfigure gmd' command, so you were probably right that that didn't need to be there.

Thanks Again !! Frank

---

