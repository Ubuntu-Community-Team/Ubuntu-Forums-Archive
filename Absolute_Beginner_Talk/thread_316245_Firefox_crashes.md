---
title: "Firefox crashes"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by stoney39 on 2006-12-10
Hi all. I'm using edgy and firefox was working fine until I wanted to log onto Stumble. Once I had logged on firefox continues to crash. It will not load up now. :confused: 
Thanks.

---

### Post by equal on 2006-12-10
It might be a good idea to go into Synaptic and uninstall/reinstall it. No, that's not a Linux way of approaching things, but dammit, I spent too long in Windows land. It might work.

---

### Post by gunksta on 2006-12-10
I doubt un-installing and re-installing FireFox will help.

Have you installed the StumbleUpon toolbar, or is it the web-site that is crashing FireFox. I am unclear which is causing you the problem.

If it's the web-site, I'm not sure what the problem is. I'm not going to get their little tool, but the main page doesn't cause my browser any problems.

If you have installed the toolbar, I suggest ripping it out of your FireFox installation. What other add-ons are you using? Are you sure this is the problem? <-- Just asking.

If FireFox will start at all, go to 
Edgy - Tools -> Addons
Dapper - Tools -> Extensions

And remove the offending extension. If FF is completely dead, it's time to get hardcore.  :-)

Go to ~/.mozilla/firefox

You should have a directory with a bunch of numbers and letters and .default. For example, mine is 4ley5032.default

Once you have identified this directory (it's probably the only one), go to it.

Now we are at
~/.mozilla/firefox/something.default/

Tell me what you have there. Hopefully StumbleUpon has created a directory with an obvious label. Delete it. (rm -rf)


If this doesn't work, I recommend nuking your mozilla install and starting over. Copy bookmarks.html to your home folder and then delete the entire something.default directory. Restart FireFox. It WILL work, but it won't remember any passwords, bookmarks, etc. You can re-import your old bookmarks, and reinstall and extensions you really like.

Maybe something in this rambling post will help.
--andy

---

### Post by stoney39 on 2006-12-10
I have stumbleupon already installed in the browser. But when I went to log into it firefox crashed and won't open again. It tries to start but crashes. I will try the your suggestions.

---

### Post by useResa on 2006-12-10
There are already several posts on firefox crashing.
I got my problems solved with the suggestion as indicated in [this thread](http://www.ubuntuforums.org/showthread.php?t=286069&highlight=firefox+crash)

Even without the additional options that were mentioned.
Hope that it will work for you too.

---

### Post by stoney39 on 2006-12-10
[QUOTE=gunksta;1869095]I doubt un-installing and re-installing FireFox will help.

Have you installed the StumbleUpon toolbar, or is it the web-site that is crashing FireFox. I am unclear which is causing you the problem.

If it's the web-site, I'm not sure what the problem is. I'm not going to get their little tool, but the main page doesn't cause my browser any problems.

If you have installed the toolbar, I suggest ripping it out of your FireFox installation. What other add-ons are you using? Are you sure this is the problem? <-- Just asking.

If FireFox will start at all, go to 
Edgy - Tools -> Addons
Dapper - Tools -> Extensions

And remove the offending extension. If FF is completely dead, it's time to get hardcore.  :-)

Go to ~/.mozilla/firefox

You should have a directory with a bunch of numbers and letters and .default. For example, mine is 4ley5032.default

Once you have identified this directory (it's probably the only one), go to it.

Now we are at
~/.mozilla/firefox/something.default/

Tell me what you have there. Hopefully StumbleUpon has created a directory with an obvious label. Delete it. (rm -rf)


If this doesn't work, I recommend nuking your mozilla install and starting over. Copy bookmarks.html to your home folder and then delete the entire something.default directory. Restart FireFox. It WILL work, but it won't remember any passwords, bookmarks, etc. You can re-import your old bookmarks, and reinstall and extensions you really like.

Maybe something in this rambling post will help.
--andy[/QUOTE

I got hardcore and it worked. I had to use the find folders option in Kubuntu but it did get me to the firefox directory and with a little looking around I found the stumbleupon extension and removed it. Now firefox is up and running. I do have another extension on it for jazz radio. I plan on removing it and reloading stumbleupon back up. I want to see if it will work then. Thank you for your help.:KS

---

