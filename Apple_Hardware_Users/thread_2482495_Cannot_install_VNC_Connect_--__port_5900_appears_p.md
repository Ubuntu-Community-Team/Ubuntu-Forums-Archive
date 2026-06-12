---
title: "Cannot install VNC Connect --  port 5900 appears perminently blocked"
date: 2023-01-02
forum: Apple Hardware Users
---

### Post by ejwjohn on 2023-01-02
I am new to the forum as I have decided to learn about Linux and am using an old Mac Mini to install Ubuntu, which appears to be working fine until I try to install VNC Connect as I must use this device in a Headless environment.

The issue appears to be linked to the installation of VNC Connect and how to release ports 5900 and 5901 to be used by VNC.

I have googled and made use of the recommendations to use the installation helper script, which appears to fail in relation to the opening up port 5900.

Within the helper script, you get an option to open up the port on the firewall... but that fails??

As I said I am not used to Linux but I have tried the Telnet cmd line to access the port and that fails.

Anyone any help on how to successfully install VNC Connect, please?

Thanks

JohnW

---

### Post by howefield on 2023-01-02
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by ejwjohn on 2023-01-02
Apologies did not notice this forum in the list.
JohnW

---

### Post by ejwjohn on 2023-01-02
Hello,

Since posting this issue, I have tried to search out more info from within this forum and I have found a few references to the fact that I may have to fully install Server Code into Ubuntu first before even considering installing Real NVC Connect, which to be honest looks a challenge for my skill set.

A little more about my environment here I use a remote.it to provide a secure connection to a few Raspberry Pi devices running Raspberry OS which all run as Headless devices, and I have VNC and SSH access set up on all.

On this particular set-up with the Old Mac Mini, i have remote SSH access working but whenever i try to access the mac min using VNC it fails with a connection error, and I can confirm this as I have already noted that the 5900 port appears to be permanently blocked on the mac Mini Ubuntu system.

So I still need help in resolving this issue, please?

Thanks

JohnW

---

### Post by #&amp;thj^% on 2023-01-02
How have you checked that 5900 port appears to be permanently blocked?
I've just used firewalld, for the longest time, so I'm partial in that regard.
But say you installed firewalld, and used this to open/add ports IE:
```
 sudo firewall-cmd --permanent --add-port=5900/tcp
success

```
After your done adding or removing Reload Firewalld to apply changes:
```
firewall-cmd --reload
```
And check again with:
```
sudo firewall-cmd --list-ports
5900/tcp

```
Now I know port 5900 is open and using tcp protocol.
NOTE: If using UFW you will need to disable that:
```
systemctl disable ufw
systemctl stop --now ufw
```
Or use:
```
sudo firewall-cmd --list-all-zones
[sudo] password for me: 
block (active)
  target: %%REJECT%%
  icmp-block-inversion: no
  interfaces: eno1 en<snip>
  sources: 
  services: 
  ports: 5900/tcp
  protocols: 
  forward: yes
  masquerade: no
  forward-ports: 
  source-ports: 
  icmp-blocks: 
  rich rules: 


```
Hope this helps a little.
EDIT: I need to add this, just helpful for newer users:
 The remote host's internal firewall is blocking port 5900. For** firewall-cmd, rules **made without the** --permanent flag** don't persist across reboots. It's not uncommon for VNC to work one day and then fail the next because port 5900 wasn't added as a permanent exception.

---

### Post by ejwjohn on 2023-01-02
OK, Thanks for the response, I must admit i am not very comfortable with executing some of these cmds, but I followed your example but changed the sequence one way... I disabled ufw first and then performed the other cmds except the last as I did not understand it.

The one big thing that is different now is that the VNC Icon now shows up on the top line menu bar (Right-Hand side), this is indeed progress but why the installation seems to have worked now I am not sure, to be honest...

However, the initial issue of the connection terminating is still there so i cannot use VNC at present.

Using your commands to check open ports I see that port 5900 and port 5901 are open which are the ones i opened.

In terms of using Firewalld going forward, i am not sure as it appears to require a lot of individual set up and as you can see i am not that confident with the Command line or Linux.

Thanks for your assistance to date

JohnW

---

### Post by #&amp;thj^% on 2023-01-03
This may help a bit, different OS mentioned, but the concept is the same: [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-remote-access-for-the-gnome-desktop-on-centos-7](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-remote-access-for-the-gnome-desktop-on-centos-7)

---

### Post by ejwjohn on 2023-01-04
OK,

thanks for all the responses... i have been silent for about 24 hrs as i decided to start over...

So i have done a clean setup of Ubuntu onto the mac Mini.

All seemed to work Ok, but in reality i now think i have gone backwards and i need to sort that out the issues, which are:

1. Still cannot successfully install RealVNC Connect, it is showing in the top line menu bar but it is not functioning and i cannot see any evidence that it is Listening on 5900 either this is using netstat command
2. I use a utility called remoteit to generate secure links to my remote and previously this utility was loading and installing perfectly within Ubuntu... but not any more and i hopefully will get a helping hand from remote it support later today.

But i have used a normal uncomplicated VNC viewer connection from one Mac at my location to the other, also in my location and that fails also with an error that there is no service running .... back to the item in 1. above.

Anyone any suggestion on other command line cmds to use to get info would be appreciated.

Thanks
JohnW

---

### Post by ejwjohn on 2023-01-26
Problem is solved VNC Real connect Server  installation no longer supports Cloud connections on a free account, you have to have an Enterprise subscription&#8230;&#8230;UNLESS you are using a RASPBERRY OS&#8230;.BUT&#8230; will it work on non RPI hardware ??? .  So now moving to Tight VNC server to give that a go.   But may then try to install Raspberry OS and see how that pans out&#8230;..

Thanks
JohnW

---

