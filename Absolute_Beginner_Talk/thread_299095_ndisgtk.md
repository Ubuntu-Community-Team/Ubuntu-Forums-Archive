---
title: "ndisgtk"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by ubantunovice on 2006-11-13
I'm in a fresh install of Ubuntu 6.10 but unable to get it to connect to the internet via my wireless home network, I suspect because it does not recognize my built-in wireless adapter. 

I thought I had my problem solved because I read in my Ubuntu book:
"As sometimes happens, manufacturers aren't 100 percent forthcoming with information or specifications to make full Linux support easy. I truly admire the incredible talent and energy of Linux developers who provide Linux with excellent drivers while working in a vendor black hole. Nevertheless, this lack of information was the impetus for the NdisWrapper project, which makes it possible to use Windows NDIS drivers via a loadable Linux kernel module. **Luckily, your Ubuntu Linux system makes this extremely easy and I'll show you how**.

Click System on the top panel and navigate to the Administration submenu. There, click the Windows Wireless Drivers menu option (command name **ndisgtk**). Because this is an administrative function, you are asked for your password to confirm. After you enter it, the Wireless Network Drivers dialog appears.

To install a Windows NDIS driver, click the Install New Driver button. A small dialog appears asking you to select an INF file. Below that is a button labeled Location. Click the button to bring up the GNOME file manager and navigate to the location of the Windows INF file that corresponds to your particular wireless card. When you have chosen your driver and returned to the dialog, click the Install button to install the driver. If you have chosen the right driver and everything has gone well, you should be back at the main window; but it now shows an installed driver and lists the hardware as present."

Very clear instructions in newbie English! Ah, but there is no "Windows Wireless Drivers menu option" in the Ubuntu 6.10 I have installed.  I tried entering the command "sudu ndisgtk" in a terminal and after accepting my password it told me that this command was unknown.

So obviously ndisgtk is not included in Ubuntu 6.10 which I downloaded from the internet and installed via the created CD. I therefore would need to download it and install it myself.  **Problem**: Because I do not yet have internet access in Linux, I would have to do this in Windows. 

Could some kind soul tell me where I need to go and what exactly I need to download (in Windows) which I could then put on a flash drive for Ubuntu to find and use when I reboot into Ubuntu? And then what I need to do to get Ubuntu to do what it needs to do with it?  Remember I am a newbie.

---

### Post by Gerard Barberi on 2006-11-13
Try this link 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

you can download the file from sourceforge

---

