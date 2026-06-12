---
title: "&quot;Default Catch!&quot; errors when booting from a G4"
date: 2007-12-26
forum: Apple PPC Users
---

### Post by rompascatole on 2007-12-26
Hello all,

I hope I have the correct forum for this problem.

I installed 7.04 from a LiveCD to a donated G4 Mac. The installation went well, although it seemed to hang a bit at the very end when asked to remove the CD before the reboot.

When I try to reboot the G4, it goes to a white screen for a long time and then the "Default Catch!" error scrolls down the screen. I used the same CD to install on a G3 and it worked fine, so I don't think it's a problem with the CD.

Nevertheless, I tried reinstaling from the Alternate CD without the graphic interface. The installation finished smoothly, but I got the same error when rebooting.

I'v searched some of the other forums, and there were solutions involving hitting "F6" or going to some command console, but I haven't been able to get these techniques to work.

I'm a newby, but I suspect that if Ubuntu can boot and function well from the LiveCD - and it does with full network capability, etc, etc -  it should be able to do so from the hard drive as well.

Is there some way of checking that the Ubuntu config installed on the computer is the same as that on the LiveCD?

I imagine someone is going to ask about the Hardware of the G4. I'm not sure! I know it has an 18 G had drive but when using the Hardware viewer on the Ubuntu admin desktop, it gave me a lot of detailed information, but nowhere did it summarise how much memory the computer had or the processor type.

One last thing, the partitioning of the HD during the installation seems to have gone well, but there was a small "unknown" partition at the beginning of the disk. I tried to delete it using the Gnome partition tool, but it couldn't be removed.

I hope I included all the relevant information to allow someone to help me.

Thanks in advance.

---

### Post by stream303 on 2008-01-21
If you can run from the LiveCD and run "top" and "lspci" in a terminal, you'll get some good info.

I wonder if your default-catch is related to the 8gb partitioning limit I've seen on google about it?  That unknown partition at the beginning of the disk is normal.

It almost sounds like your donated Mac might be a system that was highly upgraded / modified without firmware updates applied possibly.

Just guessing here.  Maybe some guys more familiar with PPC hardware can jump in.

---

