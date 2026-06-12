---
title: "Firefox won't connect, 6.10"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by azurehi on 2007-03-01
Second installation of ubuntu 6.10:  firefox will not connect to any website.  DHCP is enabled; cookies are enabled; connection indicator (circle of turning dots - don't know what this is called) runs endlessly.  In my previous installation of 6.10, I did not experience this problem.

This installation is from a new 6.10 download:  installation form the 1/07 and 2/28 download present the same problem.  In XP, a variety of browsers work normally.  I had hoped to begin using ubuntu but cannot if I cannot connect.  Any help/suggestions greatly appreciated.:confused:

---

### Post by in_flu_ence on 2007-03-01
Have you verify that your download is properly burned? as in verifying that there is no data loss during the download etc?

I had experience where the whole installation runs but that there are some broken package during downloading.

Maybe you can try uninstalling Firefox and reinstall it via the network? Just some thought. Might or might not work.

Nevertheless, don't give up on Ubuntu. I think it works great even compared with other distro.

---

### Post by Sentinel83 on 2007-03-01
azurehi,

If you open a terminal can you ping an external site, google.com or yahoo.com, etc?  If you can't get a ping, can you check to make sure your main nic card is up - 

type -```
 ifconfig eth0 
```

and view the details of the IP/DHCP setup.

do other applications connect to the internet besides firefox?

---

### Post by Pedal_Pusher on 2007-03-01
azurehi,

I had a very similar problem :-

I found some info in a thread from mikeman ( #367498 ) which had been supplied by ubunutgoz :-

try disabling ipv6

a - in FIREFOX browser type about:config
b - in the Filter bar (just below address bar) type ipv6
c - in the next window down (preferences), you'll see a single line network.disable.Ipv6
, double click until it is bold and the value is true.

This got my Firefox working well but I still can't get update manager, synaptic, apt-get or aptitude to work - they just timeout.

Please let us know if this fixes Firefox for you and whether or not you can do software installs or updates (preferably via synaptic).

---

### Post by azurehi on 2007-03-01
> **Sentinel83 said:**
> azurehi,

If you open a terminal can you ping an external site, google.com or yahoo.com, etc?  If you can't get a ping, can you check to make sure your main nic card is up - 

type -```
 ifconfig eth0 
```

and view the details of the IP/DHCP setup.

do other applications connect to the internet besides firefox?

In terminal:  ping ubuntu, google, yahoo, etc. leads to endless list of ping attempts (I think); in networking or network solutions, cannot ping.  
ifconfig eth0  produces a number of line of text, beyond my understanding - did not copy but will if necessary.

"try disabling ipv6

a - in FIREFOX browser type about:config
b - in the Filter bar (just below address bar) type ipv6
c - in the next window down (preferences), you'll see a single line network.disable.Ipv6
, double click until it is bold and the value is true."  - suggestions from Pedal_Pusher":
when I type about:config FF says url not valid.

Don't understand why I am having this problem when I did not before.  Problem is also true for live cd of kubuntu, xbuntu, ubuntu 6.06 disc fron Canonical):(

---

### Post by gmutt on 2007-03-01
> **azurehi said:**
> In terminal:  ping ubuntu, google, yahoo, etc. leads to endless list of ping attempts (I think); in networking or network solutions, cannot ping.  
ifconfig eth0  produces a number of line of text, beyond my understanding - did not copy but will if necessary.

"try disabling ipv6

a - in FIREFOX browser type about:config
b - in the Filter bar (just below address bar) type ipv6
c - in the next window down (preferences), you'll see a single line network.disable.Ipv6
, double click until it is bold and the value is true."  - suggestions from Pedal_Pusher":
when I type about:config FF says url not valid.

Don't understand why I am having this problem when I did not before.  Problem is also true for live cd of kubuntu, xbuntu, ubuntu 6.06 disc fron Canonical):(

Had same problem with Kubuntu 6.10 ..Disableing IPV6 seemed to do the trick

---

### Post by azurehi on 2007-03-01
Thanks:  firefox problem appears Solved.  Typed:  about:config and this time got the list, entered ipv6 and toggled.  Firefox works well, now.  :)

---

### Post by Pedal_Pusher on 2007-03-02
Glad to hear that Firefox is now OK.

Can you update any software via synaptic, update manager, apt-get or aptitude ?

If so I would dearly like to know how ....

Thanks

---

### Post by silkstone on 2007-03-02
If IPv6 is causing a problem elsewhere, you can disable it completely in Ubuntu rather than just in Firefox. I've taken this from older posts about the IPv6 issue...

Start the terminal and type: sudo getedit /etc/modpro.d/aliases

Find the line: alias net-pf-10 ipv6

Change this to: alias net-pf-10 off

and save the file.

One posts suggests that you may have to change it to: ..... off ipv6

Try it and see if either works.

P.S. You have to reboot after making the change.

---

### Post by Pedal_Pusher on 2007-03-02
Hi Silkstone,

I have seen the suggestions about disabling ipv6 in /etc/modprobe.d/aliases and tried them without success.  I have also added ipv6 to the list in /etc/modprobe.d/blacklist  and commented it out from /etc/hosts.

Software updates still fail consistently.  I feel that it cannot be a fundamental problem (I can access the web via Firefox) but I can't solve it.  I must get it sorted out if I am to break free from XP altogether.

Just one of the joys of being a newbie I suppose ....

Thanks for your time

Regards

---

