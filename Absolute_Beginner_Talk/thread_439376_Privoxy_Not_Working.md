---
title: "Privoxy Not Working?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-05-10
Greetings,

I have had Tor for awhile, and just got around to installing Privoxy.
I read how you're supposed to make it work, from here:
[http://ubuntuforums.org/showthread.php?t=10825](http://ubuntuforums.org/showthread.php?t=10825)

But it doesn't seem to be working.

I added the > forward-socks4a / localhost:9050 .
to the */etc/privoxy/config* file, restarted Privoxy with:
> 
$ sudo /etc/init.d/privoxy stop
$ sudo /etc/init.d/privoxy start

and I do have my settings correct in Firefox, I do believe.
I have the Tor Button Extension for Firefox, and here is my settings:
* Use the recommend proxy settings for my version of Firefox
   * Use Privoxy

Now, I go to whatismyip.org, it sits there, and loads and loads, and finally Privoxy comes up saying it couldn't access the page. Tor is running, Privoxy is running. I have no idea what to do. Any Suggestions?

Sincerely,
Dr Small

---

### Post by Dr Small on 2007-05-10
Ok. After doing an analisis on my situation, I have come to reason that it is not Privoxy that isn't working, but tor. So, if anyone could, would you please suggest a site where I can easily install tor from? Apt-Get must have an old version or something.... Yet, I can't figure out how to use the ones from tor.eff.org

Dr Small

---

### Post by enthusaroo on 2007-05-11
I'm actually also stuck with the exact same problem right now as the original poster. Please help. I'm in China (though not Chinese) and I'm sick of the Chinese government blocking everything from Google to MySpace (today). :(

---

### Post by Dr Small on 2007-05-11
I solved my problem.
I went to tor.eff.org and downloaded the source tarball, installed it, and had to install libevent too. So, enthusaroo, here is a shell script I wrote up that automatically does everything that you are supposed to do manually.

It will install libevent and tor, and in the end, you should be able to run tor :D
Least ways, it worked for me.
Notice, you must have privoxy installed FIRST! This script doesn't install Privoxy, just libevent and tor.

Sincerely,
Dr Small

PS> Place "tor.sh" into your "Home Folder" (/home/yourusername/) and open the terminal and type:
```
sh tor.sh
```

---

### Post by Cuppa-Chino on 2007-09-16
how do I ensure that everything the shell script installed is removed?

---

### Post by pjbgravely on 2007-09-24
I found another fix after I compiling tor failed.

[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian]("http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian")

Remember to change <DISTRIBUTION> to what ever you are using, not sure about gutsy but it works for dapper.

Paul

---

