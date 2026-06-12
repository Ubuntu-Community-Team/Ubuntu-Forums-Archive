---
title: "Difficulty uninstalling a package"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by ghicking on 2007-04-20
Hi all

I downloaded  and installed the wrong version of AVG anti-virus by mistake.  I found the installed file in Synaptic and marked it for removal.  I got this error message:

subprocess pre-removal script returned error exit status 150

What else can I try?

Thanks

Graham

---

### Post by Sef on 2007-04-20
> downloaded and installed the wrong version of AVG anti-virus by mistake. 

How did you install AVG originally?

---

### Post by ghicking on 2007-04-20
I downloaded the .deb file and used dpkg.  Unfortunately, I downloaded the mail server version instead of the desktop one.

Regards

---

### Post by compiledkernel on 2007-04-20
Open Synatpic and search for it there. 

Should be able to remove it from that point forward.

---

### Post by ghicking on 2007-04-20
It was Synaptic that gave me the error message.

Regards

---

### Post by darrenm on 2007-04-20
Can you post the output of the terminal section of Synaptic when it fails?

---

### Post by ghicking on 2007-04-20
I hope this is the correct message - its from the pop-up window of the Synaptic GUI

E: avg75lms: subprocess pre-removal script returned error exit status 150

Regards

---

### Post by darrenm on 2007-04-20
give this a try:

```
sudo dpkg -r --force-all avg75lms
```

---

### Post by ghicking on 2007-04-20
This is the outcome of dpkg -r force-all:

(Reading database ... 129556 files and directories currently installed.)
Removing avg75lms ...
 * Stopping avgdkill: 246: Illegal number: -
local: 246: 6155: bad variable name
( not running)
 *                                                                       [fail]
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing avg75lms (--remove):
 subprocess pre-removal script returned error exit status 150
Errors were encountered while processing:
 avg75lms

The deb file is still in Synaptic - I remembered to reload!

Regards

---

### Post by darrenm on 2007-04-20
try ```
sudo rm -f /etc/init.d/avgd
sudo touch /etc/init.d/avgd
```

Then try the dpkg command again.

---

### Post by ghicking on 2007-04-20
Success!

I followed three sets of advice to complete this:

sudo rm -f and sudo touch on the etc/init.d/avgd file
I ran the dpkg routine again
I finished by running Synaptic which cleared out the bits

Great support from a great community.
Thanks again
Graham

---

### Post by Cloudedbrains on 2007-05-24
I installed AVG but because it won't let me update I want to remove it but get the same error in synaptic !!

[IMG]http://i112.photobucket.com/albums/n200/Cloudedbrains/Screenshot-2.jpg[/IMG]

Tried the terminal lines given here and get the following error:
[B]dpkg - warning: ignoring request to remove avg75lms which isn't installed.
[/B]

[SIZE="5"]HELP !![/SIZE]

---

