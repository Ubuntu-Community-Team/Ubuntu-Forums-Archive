---
title: "ppa.launchpad.net"
date: 2009-02-10
forum: Apple Hardware Users
---

### Post by caustic386 on 2009-02-10
After a mostly successful install of Ubuntu 8.10 using Wubi, i'm trying to get the sound and keyboard backlight running...  When I get to this step:

Screen backlight controls F1 - F2 work, but the keyboard backlight doesn't work. To fix it, you need to install the "hal-applesmc" from the Mactel PPA. To do this, go to System -> Administration -> Software Sources, click on "Third-Party Software" and Add (or select) the lines:

[http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) intrepid main
[http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) intrepid main (source code)

and close. 


I run into problems... Ubuntu reports that it can't connect to that repository?  It won't let me 'add' those addresses until I put 'deb' in front of them - is that the right move?  I can open these sites in Firefox with no issue... I thought maybe the issue is because I'm running the amd64 release of 8.10, and this repository is for x32?  Don't know if the repositories work that way, I'm new to all this... Thanks!

---

### Post by flaggh on 2009-02-10
You would enter it like this:

```
deb http://ppa.launchpad.net/mactel-support/ubuntu intrepid main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu intrepid main
```

---

### Post by Chrisj303 on 2009-02-10
This reminds me.

I've been having problems with the PPA for a LONG time.

After you have added the sources, and reloaded, this error always comes up -

> GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8DB7F87A2B97B7B8GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2BA7BC59D745C5EBGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFFFailed to fetch [http://ppa.launchpad.net/mactel-support/ubuntu/dists/intrepid/(source/binary-i386/Packages.gz](http://ppa.launchpad.net/mactel-support/ubuntu/dists/intrepid/(source/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/mactel-support/ubuntu/dists/intrepid/code)/binary-i386/Packages.gz](http://ppa.launchpad.net/mactel-support/ubuntu/dists/intrepid/code)/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by hyperboloid on 2009-02-10
> **Chrisj303 said:**
> This reminds me.

I've been having problems with the PPA for a LONG time.

After you have added the sources, and reloaded, this error always comes up -

Look here for the solution: [https://wiki.ubuntu.com/MactelSupportTeam/PPA]("https://wiki.ubuntu.com/MactelSupportTeam/PPA").

---

### Post by caustic386 on 2009-02-10
> **hyperboloid said:**
> Look here for the solution: [https://wiki.ubuntu.com/MactelSupportTeam/PPA]("https://wiki.ubuntu.com/MactelSupportTeam/PPA").


I see that you're running MBPro 4,1 - how's your experience been so far?  I knew it was going to take a little legwork, but I'm starting to question if it's worth it when you consider that OS X is just linux anyway?

---

### Post by Rog-Mahal on 2009-02-10
Not Linux, [Unix.]("http://en.wikipedia.org/wiki/Mac_OS_X") It's still proprietary and closed source.

---

### Post by caustic386 on 2009-02-10
While I appreciate the clarification, it didn't really offer much in the way of an actual answer?

---

### Post by flaggh on 2009-02-10
> **caustic386 said:**
> While I appreciate the clarification, it didn't really offer much in the way of an actual answer?

I hope this doesn't come off the wrong way, but there's already plenty of threads discussing this issue.  No need to hijack this one.

---

### Post by Chrisj303 on 2009-02-11
> **caustic386 said:**
> I see that you're running MBPro 4,1 - how's your experience been so far?  I knew it was going to take a little legwork, but I'm starting to question if it's worth it when you consider that OS X is just linux anyway?


I'm running a MBP4,1 - and TBH think its well worth the effort.

All the important stuff will work out-of-the-box. And you can have everything else running in around 1/2 an hour.

Its seems a LOT more stable then it used to be. I haven't had any random crashes/hardware stop working at all.
why not just give it a go on a small partition? Its easy to get rid of if you don't like it........

---

### Post by cyberdork33 on 2009-02-11
yea they changed the ppas up a little while back. you have to use the keys now.
If you tell us what page you were reading someone could fix it.

---

