---
title: "How do I install Firefox 2.0.0.3 from source?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-06
I just downloaded Firefox 2.0.0.3 from [http://www.mozilla.com/en-US/](http://www.mozilla.com/en-US/) . 

I have no idea how I am to install it.

Do I compile it? If so, how?

---

### Post by aysiu on 2007-04-06
Why did you download it? Why do you want to install it from source?

If you're using Edgy Eft (6.10), as your profile seems to indicate, you can install Firefox through Adept Package Manager or through [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get install firefox
``` If you like the Mozilla version better, this script will help you get it installed: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by confused57 on 2007-04-06
Why not use this script to install the new Firefox?:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Official_Mozilla_Build_of_Firefox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Official_Mozilla_Build_of_Firefox)

Download the script, copy & paste a few commands, then you'll have the new Firefox installed.

Added:  Aysiu beat me to it by a matter of seconds...it's the same script though, I think.

---

### Post by aysiu on 2007-04-06
> **confused57 said:**
> it's the same script though, I think. It is exactly the same script. In fact, if you look carefully at the Psychocats page, it links directly to the pykeylogger site.

---

### Post by confused57 on 2007-04-06
> **aysiu said:**
> It is exactly the same script. In fact, if you look carefully at the Psychocats page, it links directly to the pykeylogger site.

Thanks, I wouldn't install the new Firefox any other way...I've installed the new Firefox many times using the script & it's worked flawlessly.

Added:  You and nanotube have really done a great job with the script, it's appreciated by me and I'm sure many others.   Think you two could get it working in Debian Etch?...just kidding, I tried it just for "the heck of it" and the script told me to forget it, won't work.

---

### Post by aysiu on 2007-04-06
> **confused57 said:**
> Thanks, I wouldn't install the new Firefox any other way...I've installed the new Firefox many times using the script & it's worked flawlessly.
Well, [it's gone through extensive testing and revision](http://ubuntuforums.org/showthread.php?t=293301).

---

### Post by wersdaluv on 2007-04-06
I downloaded it because I think it was the only source where I can get the latest Firefox version. Is it that way, or can I get the 2.0.0.3 version from other sources?

---

### Post by aysiu on 2007-04-06
> **wersdaluv said:**
> I downloaded it because I think it was the only source where I can get the latest Firefox version. Is it that way, or can I get the 2.0.0.3 version from other sources?
You can get 2.0.0.3 from the script we've been talking about. 

If you're using 64-bit Ubuntu, you can install [the latest Swiftfox using this other script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox).

If you are using 64-bit Ubuntu and do not like Swiftfox or if you are using PowerPC Ubuntu, you may have to compile from source. Otherwise, just use the aforementioned script.

---

### Post by confused57 on 2007-04-06
> **wersdaluv said:**
> I downloaded it because I think it was the only source where I can get the latest Firefox version. Is it that way, or can I get the 2.0.0.3 version from other sources?
Since you're using Edgy, your Firefox will be updated(if it hasn't already) to 2.0.0.3 from the repositories via an update.

The script will install the latest Firefox, same as the one from the source file you downloaded.

Added: A few seconds late again, I'm typing fast as I can.

---

### Post by wersdaluv on 2007-04-06
Out of curiosity, how do I install the .tar.gz from mozilla.com?

---

### Post by aysiu on 2007-04-06
> **wersdaluv said:**
> Out of curiosity, how do I install the .tar.gz from mozilla.com?
Well, if you don't like the script (don't know why you wouldn't), then [this link](http://ubuntuforums.org/showthread.php?t=330386) outlines all the other ways you can install the .tar.gz from Mozilla.

---

