---
title: "what does koti.mbnet mean?"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-05-19
[http://theli.free.fr/packages/breezy/./Packages.gz:](http://theli.free.fr/packages/breezy/./Packages.gz:) 404 Not Found
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:) 404 Not Found
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:) 404 Not Found


this is not alowing me to upgrade to dapper. what is this please?

W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found

---

### Post by halitech on 2006-05-19
[QUOTE=sophtpaw]W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var /lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such fi le or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/ apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or di rectory)


this is not alowing me to upgrade to dapper. what is this please?[/QUOTE]


it's two of the source file locations but it is looking for breezy update files so if you are trying to update to dapper, you need to edit your sources.list so everything says dapper instead of breezy

---

### Post by sophtpaw on 2006-05-19
[QUOTE=halitech]it's two of the source file locations but it is looking for breezy update files so if you are trying to update to dapper, you need to edit your sources.list so everything says dapper instead of breezy[/QUOTE]

I was just following the instructions given here:

[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

Is there an easy way to change sources.list other than doing it all by hand one by one?

thx 

--

---

### Post by halitech on 2006-05-19
if you do:

   sudo gedit /etc/apt/sources.list

then click the replace button, you can select breezy as the word to replace and dapper as the replacement word, then save and do the sudo apt-get dist-update and sudo apt-get dist-upgrade

---

### Post by halitech on 2006-05-19
maybe check this thread out for more info

[http://www.ubuntuforums.org/showthread.php?t=179400]("http://www.ubuntuforums.org/showthread.php?t=179400")

---

### Post by catlett on 2006-05-19
Your link's information works. The update manager -d worked for me. That source list  shouldn't be a problem. But the upgrade might.
For your reference here are 2 threads started by me about how to upgrade and what happened when I did. 
[http://www.ubuntuforums.org/showthread.php?t=177692](http://www.ubuntuforums.org/showthread.php?t=177692)
[http://www.ubuntuforums.org/showthread.php?t=178903](http://www.ubuntuforums.org/showthread.php?t=178903)

---

### Post by sophtpaw on 2006-05-20
[QUOTE=catlett]Your link's information works. The update manager -d worked for me. That source list  shouldn't be a problem. But the upgrade might.
For your reference here are 2 threads started by me about how to upgrade and what happened when I did. 
[http://www.ubuntuforums.org/showthread.php?t=177692](http://www.ubuntuforums.org/showthread.php?t=177692)
[http://www.ubuntuforums.org/showthread.php?t=178903](http://www.ubuntuforums.org/showthread.php?t=178903)[/QUOTE]
i don't know what this koti business is. How do i correct it?

---

### Post by user1397 on 2006-05-20
why don't you just delete those lines from your sources.list?

---

### Post by sophtpaw on 2006-05-20
[QUOTE=erik1397]why don't you just delete those lines from your sources.list?[/QUOTE]

ERrr...maybe they are important? I don't know what they are. However, If something is in sources list i presume it is there for a reason?

But i like your line of thinking. If something is broken just dump it:D

---

### Post by user1397 on 2006-05-20
[quote=sophtpaw]ERrr...maybe they are important? I don't know what they are. However, If something is in sources list i presume it is there for a reason?

But i like your line of thinking. If something is broken just dump it:D[/quote]
it's completely fine if you delete them. i've done it, and everything is ok. it wouldn't be anything important...all the important ones are the ones with "ubuntu" and "security" and "archive" and stuff like that. koti is prob some automatix crap to grab a non-important deb from an obscure place!

---

### Post by sophtpaw on 2006-05-20
[QUOTE=erik1397]it's completely fine if you delete them. i've done it, and everything is ok. it wouldn't be anything important...all the important ones are the ones with "ubuntu" and "security" and "archive" and stuff like that. koti is prob some automatix crap to grab a non-important deb from an obscure place![/QUOTE]
ok, man - i trust you :roll:

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) dapper/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) dapper/

But anyone know what these lines are responsible for? Erik, the important ones have ubuntu in 'em? Well, i do see ubuntu in both lines?

---

### Post by catlett on 2006-05-20
Those lines are urls for a server. The server URLs are are where Synaptic Package Manager goes for packages (the applications that are listeed in it's menu)
The [http://koti.mbnet.fi](http://koti.mbnet.fi) is just one of many URLs that synaptic can use for packages. If I'm not mistaken the koti URLs are from Automatix and are not needed for the Ubuntu system to run properly.
The error message you get isn't a vital message. All it means is that the koti server cannot be accessed. It doesn't "break" or "stop" synaptic.
Erik is correct when he says erase them. This is an option. There is another option that will also keep that url easily accessable in case you want to access it later. In linux a ""#" in front of a line of text comments the line out. Meaning the line of text will be ignored.
In the terminal type```
 sudo gedit /etc/apt/sources.list
``` This will open your synapric repository list in an editable text. You will see alot of entries. Look for the ones with koti.mbnet and either erase the entire line of text or put a # in front of the line. Hit "save" on the window controls and your done.
 ```
sudo apt-get update
``` There shouldn't be any errors when it reloads the cache.

---

### Post by sophtpaw on 2006-05-20
[QUOTE=catlett]Those lines are urls for a server. The server URLs are are where Synaptic Package Manager goes for packages (the applications that are listeed in it's menu)
The [http://koti.mbnet.fi](http://koti.mbnet.fi) is just one of many URLs that synaptic can use for packages. If I'm not mistaken the koti URLa are from Automatix and are not needed for the Ubuntu system to run properly.
The error message you get isn't a vital message. All it means is that the koti server cannot be accessed. It doesn't "break" or "stop" synaptic.
Erik is correct when he says erase them. This is an option. There is another option that will also keep that url easily accessable in case you want to access it later. In linux a ""#" in front of a line of text comments the line out. Meaning the line of text will be ignored.
In the termenail type```
 sudo gedit /etc/apt/sources.list
``` This will open your synapric repository list in an editable text. You will see alot of entries. Look for the ones with koti.mbnet and either erase the entire line of text or put a # in front of the line. Hit "save" on the window controls and your done.
Rub ```
sudo apt-get update
``` There shouldn't be any errors when it reloads the cache.[/QUOTE]

Thanks for reassuring me. I've put the # infront, so thats cool now. I've replaced breezy with dapper and should now be able to  upgrade to the Dapper One

---

### Post by mcduck on 2006-05-20
So Automatix really uses some repository in mbnet.fi? That's insane, it's the slowest and crappiest server even for us that actually live in Finland :D

If that's true I'll sure keep safe distance to Automatix..

---

### Post by catlett on 2006-05-20
[QUOTE=mcduck]So Automatix really uses some repository in mbnet.fi? That's insane, it's the slowest and crappiest server even for us that actually live in Finland :D

If that's true I'll sure keep safe distance to Automatix..[/QUOTE]
I'm almost positive. I changed my list back and have reinstalled since using Automatix so I don't have the listing to check against, but Automatix changes your list to theirs after you use it. That repo used to be in mine and I used Automatix in the beginning so I'm almost positive that is an Automatix repo. It seems (myself included) that Automatix adds repos that come up with errors afterwards. 
Your post clears it up. I'm ignorant about the diferent servers but I always wondered why koti kept throwing up errors.
I've gotten better with my linux box and didn't use Auto.. after my last install. I use the debian multimedia repo and apt-get everything I need.

---

