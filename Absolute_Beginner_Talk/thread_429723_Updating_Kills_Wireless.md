---
title: "Updating Kills Wireless"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by d33p on 2007-05-01
Ok, hoping posting here will get some answers.  I have a Thinkpad T40 with the Cisco Aeronet wireless card.  Ubuntu 6.06 live cd worked fine, I installed the OS, and everything was peachy.  After the update manager downloaded all the current updates, I rebooted.  The wireless was then not found in the network manager menu, only wired ethernet and dial up modem.  Since then, I have tried re-installing it several times.  Half the time, the wireless comes back, but then disappears again after update.  The rest of the time, it is actually still missing after the install.  I have seen various posts about wireless disappearing after updates, but so far, no suggestions on how to remedy it.  Should I go with Feisty (is this still an issue?).  This is a great OS so far, but having to continually re-install and configure, only to have it rendered moot is quite vexing.  The culprit seems to be the Synaptic updates, as the wireless is fine as long as I never update.  Any help would be great.

                                                   D33p

---

### Post by Kobalt on 2007-05-02
If you installed your wireless compiling such things like ndiswrapper then after a kernel update (which you must experience after installing Dapper) then you need to recompile it with the headers from your newly used kernel (used after a reboot). If this is your case, make sure to have the linux-headers-`uname -r` package installed then.

If you installed your wireless another way then please describe it so that we can help you out.

---

### Post by d33p on 2007-05-02
First of all, thank you very much for your response.  I literally have nothing to go on.  I did not install or otherwise configure my wireless network card, it was autodetected out of the box by  Dapper.  Everything was fine, it enabled me to configure and connect to my network using the Network Manager (I am assuming that is what it is called).  The Network Monitor Applet initially displayed the connection Lo, but removal of the applet from the toolbar and then putting it back solved that problem.  I tried to find out at what point the wireless stopped working, and determined that it was not even updating all the initial packages, but instead was the enabling of the additional repositories (Universe, Multiverse, Backports, etc.) and rebooting.  I tried editing the blacklist file, but to no avail.  iwconfig gives me a list that does not include eth1, and ifconfig gives me the connection lo, and nothing else.  I specifically edited etc/network//interfaces and commented out all the connections except eth1, but again to no avail.  In device manager, the Cisco Aironet is still viewable, but it is not active.  The device eth1 is shown as not found.  I am hoping I can get *somewhere* to start, and I am completely open to ideas.  Thank you very much,

                                                       D33p

---

### Post by Kobalt on 2007-05-02
I think this can come from Network-Manager, since it requires the wireless interface to carry the wlan0 flag and nothing else.
I've given up using this tool since it literally made my life much more complicated that it was before. Try to disable it and uncomment your interfaces in /etc/network/interfaces then restart your network with ```
sudo /etc/init.d/networking restart
```
I bet you'll get better results without Network-Manager.

And for what it's worth, I get a better signal (+20%) without NM on the exact same connection...

---

### Post by dca on 2007-05-02
network-manager is buggy in most distro(s), I too have stopped using it.  The only solution I've found for heavy mobile/laptop use is add the network applet to the taskbar for your NIC and then install 'wifi-radar' and use that for wireless config...

---

### Post by dca on 2007-05-02
Oh, be sure to drag a copy (wifi radar) from your Applications menu to the tray up top after installation...

---

### Post by d33p on 2007-05-03
Thanks for the suggestions so far.  I am going to disable network manager, and see what happens.  Can I disable it in symantic, or do I need to do a command line script?  Thanks.

                                                      D33p

---

### Post by dca on 2007-05-03
Open synaptic and search for network-manager or network-manager-gnome, right-click, and select complete removal...  WiFi-Radar is avail in one of the repos...

---

