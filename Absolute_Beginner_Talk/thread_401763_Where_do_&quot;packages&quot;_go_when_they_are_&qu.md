---
title: "Where do &quot;packages&quot; go when they are &quot;installed&quot;?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by tdutta on 2007-04-05
Hi there,

New to Ubuntu Dapper. Trying to install some basic programs. Tried to use easy ubuntu but I'm not sure it worked. How can I verify that what I've installed is actually on my system? Is there a way to look at the list of applications available to me? Why are they not updated into the applications menu after installation?

In particular, I tried to install a flash through easy ubuntu but when i go to youtube, I still can't see videos.

Any ideas?

Thanks,
Tilak

---

### Post by ubuntu27 on 2007-04-05
Now the opinions on this differ. I believe that a new user should install or configure their computer without a help from special applications such as "EeasyUbuntu" or "Automatix" since people won't be able to learn about their new Operating System by using them. 

Here is a little guide for installing software in Ubuntu.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)



Follow this guide for installing restricted formats such as Flash, MP3, etc.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by user1397 on 2007-04-05
> **ubuntu27 said:**
> Now the opinions on this differ. I believe that a new user should install or configure their computer without a help from special applications such as "EeasyUbuntu" or "Automatix" since people won't be able to learn about their new Operating System by using them. 

Here is a little guide for installing software in Ubuntu.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)well that argument is debatable.  isn't copying/pasting stuff into a terminal just as easy as clicking stuff on automatix?

great guide on installing stuff: [http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)

As to answer you question, OP, packages downloaded from the ubuntu repositories go to a special directory, which I think is in /etc/apt/??? (i kinda forgot)

---

### Post by deadgobby on 2007-04-05
Most of the files are save in etc folder. So that would be Places>File System>Etc

---

### Post by tdutta on 2007-04-05
Thanks deadgobby...but I'm confused...

I go into my 'places' menu...but there isn't a 'file system item'...am i looking in the wrong place?

-T

---

### Post by Zero Prime on 2007-04-05
> **ubuntuman001 said:**
> well that argument is debatable.  isn't copying/pasting stuff into a terminal just as easy as clicking stuff on automatix?

great guide on installing stuff: [http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)

As to answer you question, OP, packages downloaded from the ubuntu repositories go to a special directory, which I think is in /etc/apt/??? (i kinda forgot)

I use Automatix, but I have to say that I have learned a lot from copying and pasting.  

As for the question, try going to /usr/bin.

---

### Post by Happy_Man on 2007-04-05
Filesystem is just another name for "computer." :)

---

### Post by LaurelLynn on 2007-04-05
Dear tdutta,

From a command prompt:

dpkg -L

list everything installed on the system

dpkg -L    package-name

will list all the files for ¨package-name¨. There will be a lot in several different folders.

It is a lot easier to stick with apt-get or synaptic for installing, removing and updateing programs.

apt-get update package-name

should be harmless, and will point out any dependancies if they are missing.

Some programs install into Gnomes menus, some are only accessible by command.

Since Flash is available as an extension for firefox, I would try to install it from the browsers menu:

Tools->Extension

If  Flash isn´t listed click on ¨Get More Extensions¨

Laurel Lynn

---

### Post by vruum on 2007-04-05
I'm not sure flash is a firefox extension as much as a plugin (not sure about the difference, though) so it's not available from the extensions site. instead try typing about:plugins in your browsers address bar. a page will show up that lists all installed plugins and which version they are. if flash is there, try going to some other site, that uses flash, eg. [http://flash.com](http://flash.com). if that works, and youtube still doesnt, it's probably just a matter of upgrading your flashplayer.

---

### Post by LaurelLynn on 2007-04-05
Your right vruum, 

Plugins and Extensions are similar, but I guess they tie in at different levels.

[https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)

Has a link to Flash, it leads to a tarball though. I know you can get it through apt-get, because I did so last week. I was following a how-to on getting DVDs to play. Flash was one of about twenty packages. Sorry can´t remember the pages address.

Laurel Lynn

---

