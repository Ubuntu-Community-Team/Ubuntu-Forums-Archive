---
title: "HOWTO: Installing Ubuntu v7.10 in Parallels Desktop v3.0 for Mac (build 5160)"
date: 2008-01-24
forum: Apple Intel Users
---

### Post by bsodmike on 2008-01-24
Hi All,

Today, in about two hours or so I managed to get v7.10 working on my MacBook Pro running 10.4.9 (Tiger).

**_This is what I did:_**

1. Boot the install CD. When the menu screen comes up press F6 for boot options before it starts the install

2. Delete the 'quiet' and '- splash' option and press the Return key to start up the installation. This will prevent the terminal window from being hidden by a splash screen so you can do the next steps.

3. The install system will begin to boot and the display server will die as before. However now it will go back and forth between the graphic display window and the terminal window. During the moments that it is in the terminal window you can type to the command shell. If it comes up with the window that says 'The display server has been shut down about 6 times in the last 90 seconds' go ahead and type Return to select the OK and you will again get the terminal window and in a few minutes get the dying display server again. 

Simply get to another 'shell' by performing: ALT+F2

4. Type the following:

> sudo killall gdm

You will now be at a shell prompt, and the gdm server has been stopped. Then using vi or pico as you prefer, edit xorg.conf as root:

> sudo pico /etc/X11/xorg.conf

5. Scroll down to the Device section (not Input Device), and insert inside it the line

Option "LVDSBiosNativeMode" "false"

...then save the file and exit the editor.

6. Start up the display server again by typing the command

> startx

This will bring up a window filled with a grey pattern. Have patience and wait, and in a minute or two you will get a real Ubuntu desktop with an Install icon on it. Double-click the Install icon to start up the install process.

7. The display server error will keep happening, but the install continues anyway. Whenever you get the 'The display server has been shut down about 6 times in the last 90 seconds' window you have to type Return again to get back to the install window. It is really annoying having to do that every few minutes, but eventually the install is completed.  **This never happened to me...**

8. However you are not yet done. If you reboot after the installation (remember to disconnect the install CD) you will still get that display server death problem. The next steps are to get rid of that:

9. Reboot the virtual machine and when it says to press ESC to get the boot menu, quickly press ESC to get the boot menu, scroll down, and **boot in recovery mode**. That gives you a root shell prompt in a terminal window.

10. Press Ctrl+Alt to get focus onto Parallels (not locked inside Ubuntu) and in Parallels' Actions menu select Install Parallels Tools. That will show you instructions on how to install the tools, and will connect the tools CDROM image.

11. At the root shell prompt, type the commands that you were shown to install the tools

mount /media/cdrom
cd /media/cdrom
sh parallels-tools.run
shutdown -r now

12. That last command reboots the virtual machine. When it comes back you should have a working Ubuntu 7.10

This is what I did, and I got a very nicely running Ubuntu...

**References:**
[LIST]
[*][http://infosonic.wordpress.com/2007/10/21/ubuntu-710-install-guide-parallels-macbook-pro/](http://infosonic.wordpress.com/2007/10/21/ubuntu-710-install-guide-parallels-macbook-pro/)
[*][http://ubuntuforums.org/showthread.php?t=618205](http://ubuntuforums.org/showthread.php?t=618205)
[*][http://www.simplehelp.net/2007/04/27/how-to-install-ubuntu-feisty-fawn-in-os-x-using-parallels-a-complete-walkthrough/](http://www.simplehelp.net/2007/04/27/how-to-install-ubuntu-feisty-fawn-in-os-x-using-parallels-a-complete-walkthrough/)
[/LIST]

Many thanks to [po0f]("http://ubuntuforums.org/member.php?u=163518") who helped me out quite a bit with a different issue regarding gcc, -ltr and -lpthreads.

Cheers
Mike

---

