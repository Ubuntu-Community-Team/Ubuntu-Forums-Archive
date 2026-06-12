---
title: "Connect to Font Server running on Solaris 10"
date: 2015-03-05
forum: Any Other OS
---

### Post by Zoltan_Lakatos on 2015-03-05
Hi,

This problem was already posted on [http://ubuntuforums.org/showthread.php?t=1536798](http://ubuntuforums.org/showthread.php?t=1536798) but there was no solution yet.
So, the problem is same, but I have Ubuntu 14.04...

I have an application running on a Solaris 10 server and I am getting the display on my Ubuntu desktop (14.04.2 trusty with kernel 3.13.0-32-generic x86_64 and unity 7.2.4). 
But the problem is the fonts don't display well. So I tried to connect to the font server running on the Solaris server. 

Firstly:
$ **xhost +**
access control disabled, clients can connect from any host

I tried all these variants:
**xset fp+ tcp/<solaris-hostname>:7100**
**xset fp+ tcp/<solaris-ip>:7100**
**xset fp+ tcp/<solaris-FQDN>:7100**

The host name resolution was ok.

Font path:
$ **xset q**
/usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,built-ins
    
But I keep getting this error:
    xset:  bad font path element (#8), possible causes are:
        Directory does not exist or has wrong permissions
        Directory missing fonts.dir
        Incorrect font server address or syntax

If I removed (**xset fp- built-ins**) the 8th of elements (built-ins), the error changed to #7 and so on...

No network problem:
#** telnet <solaris-ip> 7100**
Trying <remotehost-ip>...
Connected to <remotehost-FQDN>
Escape character is '^]'.

I verified that the font server is running on the Solaris server this way:
bash-3.2# **netstat -an | grep 7100**
          *.7100               *.*                0      0 49152      0    LISTEN
    <solaris-ip>.7100   <ubuntu-ip>.48015  29312      0    49232      0 ESTABLISHED

That was the telnet connection...
    
    bash-3.2# **cat /etc/*release**
                        Oracle Solaris 10 8/11 s10x_u10wos_17b X86
      Copyright (c) 1983, 2011, Oracle and/or its affiliates. All rights    reserved.
                                Assembled 23 August 2011

I have more of a Debian (Wheezy) system, which works well...

I have Googled for the last days on this without finding any answer. So this is my last resort! Any help will be really appreciated... 


Thanks in advance! 


[Alternatively, is there some way to install the Solaris fonts on Ubuntu?]

---

### Post by Zoltan_Lakatos on 2015-03-06
The alternative "resolution" is very primitive:
I just copy all fonts from font server to all Ubuntu clients...
[B]mkdir /usr/share/fonts/sun
scp -r root@<solaris-ip>:/usr/openwin/lib/X11/fonts/ /usr/share/fonts/sun/[/B]
**fc-cache -fv**

Create an extension for the xorg.conf:
**vi /etc/X11/xorg.conf**
Section "Files"
            FontPath        "/usr/share/fonts/sun/Type1"
            FontPath        "/usr/share/fonts/sun/F3bitmaps"
            FontPath        "/usr/share/fonts/sun/Speedo"
            FontPath        "/usr/share/fonts/sun/misc"
            FontPath        "/usr/share/fonts/sun/TrueType"
            FontPath        "/usr/share/fonts/sun/75dpi"
            FontPath        "/usr/share/fonts/sun/100dpi"
    EndSection


That's it!

(**tcpdump -n dst port 7100** shows Ubuntu client doesn't connect to Solaris, when I use the **xset fp+ tcp/<solaris-ip>:7100**)

---

