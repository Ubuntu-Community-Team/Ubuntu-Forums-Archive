---
title: "Networking Ubuntu and iMac"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Larry Roll on 2007-04-14
I'm running Ubuntu 6.06 Dapper on a Dell Pentium IV 3 GHz, 1 GB RAM, on an ethernet network using a Linksys wired router.  I also have my new 20" iMac on the same network.  I'd like to get the two computers "talking" to each other for purpose  of file sharing and perhaps sharing an HP 2575 all-in-one printer/scanner/copier.  

I'll provide any information required, but will require ste-by-step instructions which do not assume any competence on my part.

---

### Post by Legionox on 2007-04-14
I don't how to get file sharing but with printer sharing visit [this post]("http://ubuntuforums.org/showthread.php?p=301574#post301574")

---

### Post by arkhitekton on 2007-04-15
Hi Larry,

I have a very similar setup with Ubuntu 6.06 LTS on a Dell Inspiron 9100 and an Apple Mac 20" running OSX 10.4.  I use sshfs (secure shell file system) to make a connection between my Ubuntu box and the Mac box.  In brief:

Get the sshfs packages using:
** sudo apt-get install sshfs**

Then the following so users can mount and unmount directories:
[B] sudo chmod +x /usr/bin/fusermount
*[addition]*
sudo chmod o+rw /dev/fuse
*[end addition]*
[/B] 
Create a directory in your Ubuntu home directory.  I've called mine "MyApple" using:
** mkdir MyApple**

[B]*[corrections]*
[/B]
Everytime you want to make a connection, load the fuse module, using:
[B]sudo modprobe fuse

[/B][B]*[end corrections]*
[/B]
Then to connect to the Apple run:
** sshfs <username on apple>@<IP address of apple>: /home/<username on ubuntu>/MyApple**
Your Apple home directory should now appear in MyApple on your Ubuntu home directory.  You will most probably be requested for your Apple user password.

To disconnect from the Apple run:
** sudo umount /home/<username on ubuntu>/MyApple**
You will be requested for you Ubuntu user password.

As you wanted explicit instructions:
subsitute <username on apple> with your Apple username;
subsitute <IP address of apple> with your Apple's IP address.  You may also be able to use the Apple's host name instead of the IP address.  However that may depend on your router.  My Apple has the very unimaginative name of new-host so I use "new-host.home" instead of the IP address;
substitute <username on ubuntu> with your Ubuntu username.

You can get quite sophisicated with this.  I have the connection and disconnection commands recorded in .bash_aliases as:
** alias mMyApple='sshfs <username on apple>@<IP address of apple>: /home/<username on ubuntu>/MyApple'**
** alias uMyApple='sudo umount /home/<username on ubuntu>/MyApple'**
[Note the quotation marks.]

***[corrections]***

In order to use the aliases, you have to automate the loading of the fuse module, by typing:
**sudo sh -c "echo 'fuse' >> /etc/modules"**
[Note the " and ' and >>]
The fuse module will now be loaded everytime your machine boots.

***[end corrections]***

Now all I have to type is **mMyApple** to mount the directory and **uMyApple** to dismount the directory.  .bash_aliases runs every time a shell is started provided it is looked for my .bash_profile.  You can use nano or gedit to edit either file.

I also use authenication by key for ssh which means I do not have to enter the password for the Apple in this instance when I mount the directory.

(I use similar arrangements to access a Linksys NSLU2 running Debian.)

Apologies if the following is not allowed on the forum.  Its not meant to be advertising just a bibliography.
I got my setup working after reading:
"Ubuntu Hacks", Oxer, Rankin, Childers, O'Reilly  2006;
"Linux Security Cookbook", Barrett, Silverman, Byrnes, O'Reilly 2003.
I realise there is a lot of free information through the forums and the Internet but I have found these both very useful (and now well worn) text books.  When I document how I've set things up I just quote the Hack #!

I hope this helps.  I've used an identical means as described in the other post to get the printer working.  On the whole I found getting the Ubuntu Dell and the Mac to work together is almost trival.  The Mac & Ubuntu to the Windows XP box is a complete nightmare.  But I'm sure that'll be another post...

---

### Post by Larry Roll on 2007-04-29
ark:

Thanks for the reply.  However, it mostly went way over my head.  Remember:  This is the Ultimate Beginner's Forum.  I am an Ultimate Beginner.  You used the term "bash."  What is that?  See, that gives you an idea of how clueless I really am.  

How do I learn the IP address of my Mac?  

I really need to be "talked down" to and have things spelled out in very specific and non-geeky terms all the way through, and I need step by step, sort of "start your terminal" and "type this at the prompt" sort of instructions.  I have no geek-smarts to speak of, and can't seem to acquire any, since I cannot get the kind of instructions which lead to the sort of learning experience which would give them to me.  How does anyone learn these things, anyway? 

I am more interested in using files from my Ubuntu computer while using my iMac, than the other way around.  I would ultimately like to learn how to do this both ways, but the learning curve is pretty much vertical for me.  

Again, I thank you for your effort, but I need some really detailed step-by-step instructions which don't presume any competence on my part.

---

### Post by arkhitekton on 2007-05-05
Hi Larry,

Sorry, I'll try to reword what I wrote so its a bit more straight forward...

On your Apple, open a Terminal (Finder -> Go -> select Applications -> select Utilities -> select Terminal.app) and then type the following
[B]hostname 
[/B]to get the name of your Apple
[B]whoami
[/B]to find out how the Apple sees your username. Use this value in place of <username on apple>.

To find out the IP address of your Apple, select the APPLE in the top left-hand corner, select About This Mac, when the window opens select Network in the Contents pane.  The IP address (aka IPv4 Address) should be shown in the right-hand column against either Airport or Built In Ethernet.  Use this value in place of <IP address of apple>.
 
Open a Terminal in Ubuntu and type the following:- 
[B]cd ~
whoami[/B]    (to get your username on Ubuntu)[B]
sudo apt-get install sshfs[/B]
**sudo chmod +x /usr/bin/fusermount**[B]
sudo chmod o+rw /dev/fuse[/B]
**mkdir MyApple**

Then in a Terminal, everytime you want to connect to the Apple type:
**sudo modprobe fuse**
[B] sshfs <username on apple>@<IP address of apple>: /home/<username on ubuntu>/MyApple
[/B] Your Apple home directory should now appear in MyApple on your Ubuntu home directory. You will most probably be requested for your Apple user password.

To disconnect from the Apple, type the following in a Terminal:
** sudo umount /home/<username on ubuntu>/MyApple**
You will be requested for you Ubuntu user password.

I hope the above helps, a bit more.

---

### Post by Larry Roll on 2007-05-23
ark:

I've just now read your revised instructions; they seem a bit more clear.  It's too late to try it now, but I will soon.  Thanks again for your help!  

Larry

---

### Post by Chet Hardin on 2007-06-04
Hey arkhitekton

I followed what you said to do closely. I am running fiesty and I have an apple running 10.4.

It seems that I set it up OK on my ubuntu machine, but I don't see anything in my myapple folder. What do I have to do to my apple?

thanks.

---

### Post by wormser on 2007-06-04
I am also trying this.  I get the following error after connecting.

> fuse: missing mountpoint

---

### Post by arkhitekton on 2007-06-04
Hi Wormser & Chet Hardin

Sorry, I'd forgotten to include some instructions regarding fuse.  I've added the corrections to my original and second post.  Hopefully it will work ok, now.

Regards

Arkhitekton

---

### Post by wormser on 2007-06-04
> **arkhitekton said:**
> Hi Wormser & Chet Hardin

Sorry, I'd forgotten to include some instructions regarding fuse.  I've added the corrections to my original and second post.  Hopefully it will work ok, now.

Regards

Arkhitekton

I tried the update and still got the same error:  fuse: missing mountpoint

Another thing I noticed is there is only a /usr/bin/fuse[COLOR="Red"]**r**[/COLOR]mount and not a fusemount.  R being the difference.  I hit tab to auto complete on the first attempts and did not notice.  I am on Feisty so they might have renamed things.  I do have the module fuse when I run a lsmod.  Could it be looking for fuser?  I am still new to linux and have not played around with modules yet.

Thanks

---

### Post by wormser on 2007-06-05
I got it working.  I just had one mount point.

---

### Post by arkhitekton on 2007-06-07
Hi wormser

You're correct.  it's fuse_r_mount.

Sorry, I'll update the above...

---

### Post by arkhitekton on 2007-06-10
Hi Larry & wormser

I've just had to rebuild my Dell 9100 Ubuntu box with 6.06 LTS and come across the same problems you appear to have.  I did not have this problem before.  I seem to have found a solution that I did not have to use previously:
[B]
sudo chmod o+rw /dev/fuse
[/B]
I've updated my posts above to show where the new command should be used.  I hope this helps.

---

### Post by Chet Hardin on 2007-06-13
Hey --

So I followed your instructions closely, but I never see my Apple home folder. I am always told after a minute or so of searching that the "remote host has disconnected". 

Does this have something to do with my Mac?

Thanks.

---

### Post by arkhitekton on 2007-06-13
Hi Chet

It sounds like it could be the Apple.

You need to have the Apple firewall set to allow SSH access to the Apple.  You can  get to the Apple firewall via System Preferences. In the Internet & Network section, select Sharing, then enable **Remote Login**.  One way to check SSH access is working is to open a terminal on your Ubuntu box and type:

[B] ssh <username on apple>@<IP address of apple>

[/B]That should start a secure shell session with the Apple.  If this is the first time you've done this you'll be asked to confirm that you want to accept the key.  Type **yes.**  Then you'll be asked for a password, so type in your Apple pasword.  After that you should have a command line similar to that you see in an Ubuntu terminal.  You can try command such as **ls** or **whoami** or **finger** or **who** to confirm you are connected to your Apple.  To close the session type **exit**.

I've also noticed that I need to make sure the Apple is awake and not asleep in order to connect to it.

...  However I'm starting to wonder if, given the problems I'm having with what was a stable set up, that something has changed in the latest kernel to stop some of the things working...

Good Luck :)

---

### Post by Chet Hardin on 2007-06-13
So, I got the networking to work. It was awesome!

Then, I shut down. Started back up. Now, I am asked to enter my password three times in a row. Then I am asked to enter my Mac password three times. Then I am told the remote host has disconnected. Bizarre, right?

---

### Post by arkhitekton on 2007-06-14
Hi Chet,

I glad to read it finally worked - however briefly!

...  What did you shut down?  Apple or Ubuntu or both?

Has something been reset following the restart?  You will have to run:
**sudo modprobe fuse**
every session before you run:
[B] sshfs <username on apple>@<IP address of apple>: /home/<username on ubuntu>/MyApple


[/B]

---

### Post by thrice_loved on 2007-08-06
I have followed the above and have had the same experience...

It worked the first time (beautifully!) but the next time I tried, I was asked for my password three times, the Mac's password twice and then it told me that "the remote host has disconnected".

HOWEVER! immediately after I had tried that, I found a network link in my 'Network' folder under my 'Places' menu. This has a little 'ssh' on the folder and when I click on it it asks me for the Mac's password (I typed that in) and it worked!

I don't yet know whether it will work every time I reboot, but it looks promising.

Thankyou for the instructions :)

---

### Post by thrice_loved on 2007-08-15
Yep, it's permanent. The link is always there in my 'Network' folder. No need to write anything in terminal I can can just go to the folder double click, type in my password and I'm in. 

I have since set this up for a second mac (a laptop) and it's working beautifully too - but you do need to remember to allow remote log-in on the Mac. :)

---

