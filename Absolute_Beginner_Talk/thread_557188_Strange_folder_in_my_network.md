---
title: "Strange folder in my network"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by iansane on 2007-09-22
Hi, I have a folder called "Bruce Lake MAC.local:22" in my network now. I cannot access it. It needs a usr name and password.
 Not sure when in the past couple of days it showed up, but I've done something maybe I shouldn't have and am thinking it might be the reason.

I enabled all  Ubuntu supported and unsupported (back-ports) updates. All of a sudden I had 39 new updates. Instead of reading up on everyone, I did like I did in Windows updates and just selected "install all updates"

Does that folder have something to do with something I installed? Before, the only thing there was the windows network icon.

---

### Post by Nikitas350 on 2007-09-22
Even if i am not an expert one (i am a newbe one), i strongly believe that the updates you install have nothing to do with the folder. To delete this folder right-click on it and select unmount volume :)

---

### Post by tie_dyed_sox on 2007-09-22
Are you using a shared PC?
This is purely a guess, but the file name "Bruce Lake MAC.local:22" suggests that someone tried to SCP (secure copy a file over a network/Internet) a folder but did it incorrectly. I'm guessing this because SCP uses port 22 (SSH protocol) and the ":22" is sometimes used as a parameter to access port 22. If this makes no sense to you at all then I apologise!
You can find out who owns it using "ls -l" in the terminal from the directory where it's located.
As for installing the updates without reviewing them - don't worry - it's not really necessary to review them if you're a newbie like me, and it's unlikely to be related to the mystery folder.

---

### Post by iansane on 2007-09-22
ok, little more info on it
from properties:

Type: desktop configuration file (strange, looks like a shared folder to me)
Size: unknown
location: network:///
Mime type: application/x-desktop
modified: unknown
accessed: unknown

privelages are read only and owner is unknown

can't open it. Not a chared PC unless Ubuntu shared it's self. If you mean do other usrs log in, no. Nobody touches it till I learn to admin security on it. Port 22 makes sence to me, like port 80 for html in windows. I just don't know anything about ssh or scp

---

### Post by iansane on 2007-09-22
> **Nikitas350 said:**
> Even if i am not an expert one (i am a newbe one), i strongly believe that the updates you install have nothing to do with the folder. To delete this folder right-click on it and select unmount volume :)

I'm in the network place and there is no unmount option. Is the folder actually in another directory somewhere?

---

### Post by tie_dyed_sox on 2007-09-22
To permanently delete the folder, open up a terminal, change to the directory where the folder is located, and enter:

sudo rm 'Bruce Lake MAC.local:22' -rf

Type in your password and that should do the trick.
Let me know if you have any problems.

---

### Post by iansane on 2007-09-22
OK I think it's time to call the ISP. Got an IP when trying to login to the folder, wrote it down this time. Did a portscan on it. (22 ssh, open). Did a trace route and the only thing between it and me is me! My IP is on the same subnet as my DHCP server. So is this correct? It's either a local ssh service from something I installed or it's a computer on my ISP's network with an open ssh port.
I am plugged straight into the dsl modem which as I uderstand it, is a passthrough straight from the ISP.

---

### Post by iansane on 2007-09-22
> **tie_dyed_sox said:**
> To permanently delete the folder, open up a terminal, change to the directory where the folder is located, and enter:

sudo rm 'Bruce Lake MAC.local:22' -rf

Type in your password and that should do the trick.
Let me know if you have any problems.

so is network an actual directory and where is it? All I'm looking at is the equivelent of network places in windows.  What directory is network located in? I have no "up option" to go to a higher level directory

---

### Post by tie_dyed_sox on 2007-09-22
Where is the mystery folder located? Is it actually on your PC or another PC/server on your local area network (e.g. In your Network Servers folder on the Desktop)? Can you provide the exact path and a directory listing? If you could take a screenshot of the folder, upload it to photoshack.com and link in your post, that might help. Try anything that might identify exactly where it came from.
It's unlikely that your ISP will be able to assist you as they probably only deal with basic issues under Windows.
Sorry for all the questions - I used to work in technical support :p

---

### Post by tie_dyed_sox on 2007-09-22
Ah, Ok... It's in your Network Servers folder.
Let me see what to do...

---

### Post by iansane on 2007-09-22
tried unplugging things and reloading the network server directory each time. In the process I got sftp://bruce-lake-mac.local and an IP. It's only one device seperating me from it so I unplugged the dsl modem, wireless router, and phone line one at a time reloading each time. It apparently is the wireless router! Well maybe not cause my wireless login doesn't work but either way, when I unplug the wireless, it changes to some kind of file that won't open and the name changes to "dnssd-local-bruce Lake MAC._sftp-ssh._tcp.local"  When I plug back in it turns into a folder again.

---

### Post by tie_dyed_sox on 2007-09-22
Have you tried right-click->unmount or delete when it's a folder/file? Does it still say "Permission denied"?
I can't find where network servers are physically located in the file system :confused:

---

### Post by iansane on 2007-09-22
yeah uh well.... This is embarrasing stupid mistake. You know in the network setup under "general" where there's a check box for "scan for and advertise local services on the network" Apparently the service (what ever it is) is from my wireless, and when I uncheck the box it goes away. I'll have to log into the router later and research it. I probly couldn't log into the folder because I have the access control list turned on for the router and since I reformated and installed Ubuntu, My host name is different. Luckily there are 2 other computers that are on the list so I can log in from one of them to allow this computer.

---

### Post by tie_dyed_sox on 2007-09-22
Glad you figured it out cos I would never have thought of that!
Yeah, you should probably keep Automatic service discovery turned off unless you're on a secured local area network and protected by a firewall... I guess.

---

### Post by iansane on 2007-09-22
thanks for the help tie_dyed

---

### Post by tie_dyed_sox on 2007-09-23
No probs, although I think I managed to confuse myself more than I actually helped!
Happy Ubuntu-ing!

---

