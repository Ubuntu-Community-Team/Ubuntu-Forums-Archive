---
title: "Bittorrent - Trouble Connecting to Tracker, connection reset by peer (previously NP)"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by CafeHarrar on 2007-03-02
Hi there!  Thanks everyone for your help so far with getting my instal running smoothly!  I am having some problems using bittorrent.  I will sometimes get an acceptable download speed, but mostly I am getting sub 5 KB/second speeds, with frequent messages about the connection to the tracker timing out, and "urlerror.  connection reset by peer."  In Windows with Azureus I usually got excellent download speeds from the same trackers, I tried using Azureus in ubuntu, but got the same problem, so for now I am just using the generic client.  My firewall doesn't show it's blocking any connections...  any ideas?

---

### Post by nudnik on 2007-03-02
> **CafeHarrar said:**
> Hi there!  Thanks everyone for your help so far with getting my instal running smoothly!  I am having some problems using bittorrent.  I will sometimes get an acceptable download speed, but mostly I am getting sub 5 KB/second speeds, with frequent messages about the connection to the tracker timing out, and "urlerror.  connection reset by peer."  In Windows with Azureus I usually got excellent download speeds from the same trackers, I tried using Azureus in ubuntu, but got the same problem, so for now I am just using the generic client.  My firewall doesn't show it's blocking any connections...  any ideas?

Linux Azureus, at least when used with Ubuntu, bites. You will notice it is not listed as a supported application by the Ubuntim. Bittorent (linux) is better, but still bites, though with slightly less pressure and dull teeth. Bittornado is the only torrent app which has performed properly for me, and on several different hardware platforms to boot. It can be installed thusly:

sudo apt-get install bittornado-gui

It sounds as if your problem may be more profound, however. Perhaps your ISP is incompatible with Linux. Is the browser sluggish as well? What about email? If the answer is yes to both, while functions which are not dependant on the internet remain unaffected, then your ISP might indeed be Anti-Torvald. Call and ask if they are Linux averse. 

I guess there is the remote possibility that Ubuntu hates your ethernet device, router or modem, but that is unlikely.

---

