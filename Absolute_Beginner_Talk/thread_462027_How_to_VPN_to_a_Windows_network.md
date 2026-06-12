---
title: "How to VPN to a Windows network?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-06-02
What is the best way to use Ubuntu to VPN to a windows network?  Using my Windows XP PC, I use the "Make a New Network Connection" wizard and then I use Remote Desktop to log in.

I looked at OpenVPN but it wants a key and secret input along with username/password.  Using my Windows PC, all I had to do was supply the IP to the gateway and my username/password.

Any help would be appreciated.

Thanks

Carl

---

### Post by cheeseborough on 2007-06-02
I've got mine working to connect to my office network from home, I found this link invaluable

[http://ubuntuforums.org/showthread.php?t=91249]("http://ubuntuforums.org/showthread.php?t=91249")

Once you've got the Network Manager installed and going, you then just click on the icon in the system tray and create a VPN link. The information you need to supply is near enough the same as for Windows; there are a lot more options, but the defaults worked for me.

---

### Post by cwmoser on 2007-06-02
I finally solved it.  That URL reference helped.

I found the problem was that I had setup my desktop Ubuntu with a Static IP.  I went and reconfigured it to have a dynamic IP adress,  and then edited /etc/network/interfaces so that it only had:
  auto  lo
  iface  lo  inet  loopback

I used '#' to comment out everthing else.

Then, lo and behold when I left click on the Network-Applet at the top of the screen in the status bar, I had a menu option titled "VPN Connections".  I put in some metrics similar to what I do with a Windows VPN and get connected.

So, the secret is a) use a dynamic IP address, and b) clean up your interfaces file.

Carl

---

