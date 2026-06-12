---
title: "Flash Plugin Locking Terminal"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by common.route on 2007-07-29
I've tried downloading the flashplugin-nonfree from the add/remove application.
When I do, it locks up when it awaits response from the adobe website.
So, any time I try to do any type of installation or update through the terminal or synaptic, I get a message telling me to enter "sudo dpkg --configure -a" into the terminal.
Whenever I do, it starts the download of flashplugin-nonfree and locks up again.

So, I tried using synaptic.
Same thing.

Then, I tried downloading the tar.gz file straight from the adobe website.
It won't download even 1% of it.




I've had no problems installing anything else, and I've even removed the ubuntu partition and reinstalled the entire OS all to no prevail and the same problem of a locked up terminal.

It's probably a problem with adobe's server or maybe a hash is incorrect or something, but either way, I'm most curious as to whether there's a command I can enter into the terminal while this thing is downloading so I can cancel it and actually have a functional terminal again.
It would be greatly appreciated if someone could help out.

---

### Post by r4ik on 2007-07-30
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

and

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

Should do the trick.

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Should be helpful also.

Good luck !

Or as root  sudo dpkg --configure -a in a terminal.

---

