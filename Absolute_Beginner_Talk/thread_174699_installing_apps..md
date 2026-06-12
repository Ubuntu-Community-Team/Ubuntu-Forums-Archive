---
title: "installing apps."
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by jdm2 on 2006-05-12
I'm having trouble installing things and I'm new to linux and ubuntu can you help me out?  Thanks

---

### Post by kart3r on 2006-05-12
what kind of "things" do you want to install?Maybe you need to activate some repositories i think. Go to Synaptic Package Manager in system -» administration -» Synaptic Package Manager then click on Settings and then Repositories then click on Edit and activate all components. That should work

---

### Post by louis_nichols on 2006-05-12
I suggest you start [here]("http://help.ubuntu.com/"). This should be your first stop when looking for answers. Some of the info there is actually found under System/help in your main menu. You'll find there more answers than you think. :) Another site where you can stop next is [the wiki]("https://wiki.ubuntu.com/"). They are both very helpful.

---

### Post by mostwanted on 2006-05-12
If you're using Ubuntu (not Kubuntu or Xubuntu) here's a graphical guide about installing intended for newbies:

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by jdm2 on 2006-05-12
I'm going to try and upload some snapshots of it.  Can you help me out?  Thanks for hte links.

---

### Post by Gustav on 2006-05-12
could you post the content of the file /etc/apt/sources.list?

(You can open the file with```
gedit /etc/apt/sources.list
```)

---

### Post by jdm2 on 2006-05-14
Thanks for the help.  Here's the output of the command.

---

### Post by catlett on 2006-05-14
First try refreshing your apt packages and then go in to synaptic```
sudo apt-get update
```
See if that helps. Another thing you can do to add more repositories is remove any "#" before a URL in your list. This uncomments then and synaptic will retrieve from them as well. The ones with the "#" have stuff that is not free in areas and some have testing stuff etc(to tell you the truth I don't know the whole run down). Most people end up uncommenting them so they can get access to more repositories.

---

### Post by jdm2 on 2006-05-14
Here's the outcome of it.

---

### Post by catlett on 2006-05-14
What's this? Is this your way of connecting to the internet.  > Could not connect to proxy-mem60fw.network.fedex.com:3128 (199.82.243.70)
Please excuse my ignorance I've had broadband connected through an ethernet card for the last 8 years I never had any network or dial up issues. So I am ignorant of these connection issues.
But that error appears to say you are not connecting to those servers. You have to get to those web sites to get the packages for synaptic.

---

### Post by jdm2 on 2006-05-14
I'm using a cat 6 ethernet cable that is hooked up to the back of a router.  All I know is I have the eth0 running under dchp and under system/administrator/network/dns it has under search domains something like the fedex.com but it's a little different.  All I know about it is that my home internet goes through there.

---

### Post by catlett on 2006-05-14
The Synaptic package manager runs off of repositories that are on servers. The manager connects to them through your internet connection. Your /etc/apt/sources.list tells Synaptic which  servers to go to.
If Synaptic can't connect to those servers it can't get the packages to install. Looking at your screenshots it appears that is  happening.
It doesn't make sense because you have an internet connection.
But if I had to guess I'd say not connecting to the repository servers is your problem.
What the solution is I don't know.

---

### Post by jdm2 on 2006-05-15
Thanks
If you got any ideas where I should be looking please tell me.  Thanks again.

---

### Post by louis_nichols on 2006-05-15
Well, I tried searching for this info, but couldn't find exactly what the search domains are. My guess is, though, that you don't really need that. So I suggest you try deleting that value (well, saving it first, just in case), and then try again.

So Synaptic says it has some problems with proxies. If the above doesn't sort you out, then you should add the search domain again and check the proxy settings for apt itself. [Here]("http://ubuntuforums.org/showpost.php?p=680024&postcount=3") is a post that explains how to correctly set the proxy for apt-get and synaptic too. Synaptic also has a dialog of it's own for this in the settings menu. In my experience, that dialog works for synaptic itself, but not for running apt-get in terminal, whereas the method in the post I linked to works for both. Now, my guess, judging from the output of the command line is that you avtually DON'T NEED a PROXY anywhere, so you should check all these settings I just wrote about to actually be... well, not set.

Of course, to take a certain step in any direction, you'd first have to find out your connection settings. DHCP is cool, but to my knowledge the protocol doesn't provide the proxy address, and Ubuntu doesn't have a unified way to set proxy either. (apt-get settings are made in one way, nautilus' is set somewhere else, gaim can read what you set in nautilus but also use a different one and so on). Still, there must be someone administering that network taht can tell you all this info.

---

### Post by jdm2 on 2006-05-15
I have just looked in the network proxy before I do what you suggested and this is what is in the automatic proxy configuration
[http://proxy-mem60fw.network.fedex.com](http://proxy-mem60fw.network.fedex.com)
I will post two screenshots of it.

---

### Post by jdm2 on 2006-05-15
in the apt.conf there is a line which is trouble me and you.  
Should it be there?  

Acquire
{
http::Proxy "http://proxy-mem60fw.network.fedex.com:3128"
}

---

### Post by louis_nichols on 2006-05-16
[QUOTE=jdm2]in the apt.conf there is a line which is trouble me and you.  
Should it be there?  

Acquire
{
http::Proxy "http://proxy-mem60fw.network.fedex.com:3128"
}[/QUOTE]

Try to comment it out!. Just put a # in front of every line you pasted. Then run apt-get update

---

