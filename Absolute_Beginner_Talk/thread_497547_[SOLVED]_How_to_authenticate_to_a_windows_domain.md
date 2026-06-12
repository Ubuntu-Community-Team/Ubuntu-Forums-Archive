---
title: "[SOLVED] How to authenticate to a windows domain?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-07-10
I have my Ubuntu laptop on my domain at work and I am trying to access a shared network resource that my account on the domain has access to.  The laptop doesn't log into the domain itself, but it didn't when I had XP on it either and I was able to browse to this share, but I can't do it from ubuntu.  Someone here told me that I needed to run a cmd that allows the ubuntu box to authenticate to this domain.  Anyone know how to do that?

---

### Post by tak1150 on 2007-07-10
Have you installed samba?

```
sudo apt-get install samba smbfs
```

Then change the domain in the config file (after backup).
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
sudo gedit /etc/samba/smb.conf
```

Find this section and change "WORKGROUP" to whatever domain you have
```
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
```

Let us know if that works for you.

---

### Post by destructchaos on 2007-07-10
go to "smb:/" and all of the available domains should be visible.  trying to access a secure domain should bring up a password dialog box where you would provide the same credentials that you did on your windows box.

---

### Post by tak1150 on 2007-07-10
Oh I forgot.

You'd have to restart the samba service

```
sudo /etc/init.d/samba restart
```

Sometimes you have to reboot your computer but you shouldn't have to.

---

### Post by kc5hwb on 2007-07-10
I've already got Samba installed, but it is configured for my home network workgroup name.

---

### Post by kc5hwb on 2007-07-10
> **destructchaos said:**
> go to "smb:/" and all of the available domains should be visible.  trying to access a secure domain should bring up a password dialog box where you would provide the same credentials that you did on your windows box.


Where do I do this?  I would go to start->run in XP, but I don't know where to do this in Ubuntu.

---

### Post by rickycodie on 2007-07-10
i think you go there in the terminal

---

### Post by destructchaos on 2007-07-10
type it into the address bar in konqueror, or whatever the equivalent is in gnome.

---

### Post by tak1150 on 2007-07-10
> **kc5hwb said:**
> Where do I do this?  I would go to start->run in XP, but I don't know where to do this in Ubuntu.

In Nautilus, click the button that says "Toggle between button and text-based location bar" to get the text-based location bar. Type

```
smb:///
```

---

### Post by twiceasworn on 2007-07-10
You should be able to navigate there in the window manager gui as well.  Although it is probably easier to do it from the terminal.  It has been quite a while since I used samba, but for me everything was pretty intuitive.  Though, I was also using the Novel client since are on Novell here at work.

When i had to set up access to my network back when I used ubunutu as my workstation OS (forced me to learn linux pretty fast :D) the network filesytems were just mounted to my filesystem.

---

### Post by undertakingyou on 2007-07-10
> **destructchaos said:**
> go to "smb:/" and all of the available domains should be visible.  trying to access a secure domain should bring up a password dialog box where you would provide the same credentials that you did on your windows box.

I have gone there in Konqueror (or Nautalis) and it shows the workgroups/domains avaliable but when I select the one that I want the server times out.  Any more info or anything special needed to be done here?

---

### Post by kc5hwb on 2007-07-10
> **tak1150 said:**
> In Nautilus, click the button that says "Toggle between button and text-based location bar" to get the text-based location bar. Type

```
smb:///
```



Ok, this is what I was already doing.  A login/authentication box never comes up.  I can see the domain, and when I click on the domain it does show me some machines, but not all of them.

---

### Post by tak1150 on 2007-07-10
> Ok, this is what I was already doing. A login/authentication box never comes up. I can see the domain, and when I click on the domain it does show me some machines, but not all of them.

The ones you cannot see are the problems and not your Ubuntu. Sounds like you need to have those "invisible" computers' networks activated.

---

### Post by kc5hwb on 2007-07-10
I am not sure what you mean.

My work PC has a shared folder that I used to be able to access from this laptop when I had XP on it, even though the laptop never logged into the domain (I had to enter DOMAIN\userid and password to get to it) Now it won't open that network share from Ubuntu.  I type in the network path, which I know well, but the login box never comes up and prompts me for a password.

---

### Post by tact on 2007-07-10
bit more info would help those who give u guidance...

I use ubuntu and of course gnome desktop.  Like you I am connected to a corporate ethernet lan and need to access netowrk shares on windows servers.   Even in the days when I used WinXP I rarely logged into the domain, rather just log into the local machine and can still access those shares.

Same for ubuntu.  You installed samba and changed the config file to a workgroup name you like.  Thats fine.  Does not have to match the office domain name - yuor home network name is just fine.

In the standard ubuntu gnome desktop to find any network shares - click on Places>Network.   In there you may see your own machine and an icon "WIndows Network".   Click on Windows Network and a list of all available domains and workgroups appears.

The appearance of any workgroup or domain in "Windows Network" is totally dependant on how windows networking works... you know the drill - machines fignt over who will be the network master browser and then all register with the masterbrowser and eventually that list of machines is propogated to all on the network.  By default (not samba, linux, or ubuntu's fault) this can take a long time!  

In windows you could take a short cut and go straight to a machine by searching for it by its name, or typing in its name and share name in the "map a network drive" dialog.

You can kinda do something similar in ubuntu...  After clicking on Places>Network>Windows Network ...  if the machine or domain you are looking for has not shown up.  You can type in the details in the entry field after like this.....    smb://your.server.name/share_name/

Dont get sucked in by the many threads here, or hits when you google, that describe long and tedious processes to get your machine to authenticate to the domain, or act as a samba server in its own right.  None of that is needed to simply access windows shares or share your own files.



Hope that helps.

---

### Post by kc5hwb on 2007-07-10
> You can kinda do something similar in ubuntu... After clicking on Places>Network>Windows Network ... if the machine or domain you are looking for has not shown up. You can type in the details in the entry field after like this..... smb://your.server.name/share_name/

This does help, yes... however this is what I am already doing, as stated earlier.  After typing smb://your.server.name/share_name/, it opens a folder and searches for a min, then it says that "not all contents within the folder can be displayed" but it never displays anything.  And it never asks me for a username/password to login.

So it sounds like I am doing it right, according to everyone's instructions, and these instructions I already knew about before making this post.  But it is NOT working the way that you say it should be, and the way that I think it should be.

---

### Post by tact on 2007-07-10
Ok ok..  we are not psychics at all, at least i am not,  and dont know what you know or dont know or how you are trying to connect til it comes out.   Yes I read your posts after my post that give more details than you had given before I wrote.

Seems the methods you are using to locate and link to shares is just fine.  Lets move on...

Not being psychic am going to have to ask apparently silly questions now (as here also no real detail given) regarding exactly how your network is set up.  

Examples:
- in all your failed attempts above are you talking about shares on your corporate domain??  or are some attempts on the domain while some are on a home LAN?   Can we focus on just one for now?
- if corporate domain, windows networking is not as simple or standard as people imagine.  the way shares are announced or made accessible varies.
- before all this lets look at the basics..  can you even ping the server you want to connect to?  what is its IP address and what is your IP address?

regards.

---

### Post by kc5hwb on 2007-07-10
As stated in my first post, I am at work, on the corporate network, but not connected to the domain.

I am not connecting to a server, I am connecting to a network share (this was also already said)

the IP of the share is 20.24.11.140 and yes I can ping it fine.

my ip is 20.24.10.26

If you have any NEW questions, be them silly or not, feel free to ask.

---

### Post by tact on 2007-07-10
I'll pass.  night

---

### Post by kc5hwb on 2007-07-10
> **tact said:**
> I'll pass.  night

thanks.

anyone who has really done this before and not just guessing?

---

### Post by destructchaos on 2007-07-10
i had a problem on my home lan connecting to shares that were connected to a different router, i.e. the share was 192.168.1.* while my laptop was 192.168.2.*.  is it possible for you to connect to the same router as those shares?

---

### Post by destructchaos on 2007-07-10
i never did figure it out and finally decided it was just another case of microsoft voodoo that was preventing me from connecting.

---

### Post by kc5hwb on 2007-07-10
I wouldn't know which router those are connecting to for sure, but I have both machines plugged into the same port on the wall.  True, they could still be routed differently, but in reality they shouldn't be.

---

### Post by undertakingyou on 2007-07-10
I missed in you previous posts that you and the network share are on different subnets.

To see across subnets you have to have a wins server running or have all the routing manually entered into the routing table.  The likelyhood is that your company uses a WINS server, and that you will need to point to that to be able to see the shares.  Also, if your company uses a DNS server I would point it to that also.

To manually add the routing I believe that you use the route command.

---

### Post by tact on 2007-07-10
> **undertakingyou said:**
> I missed in you previous posts that you and the network share are on different subnets.

To see across subnets you have to have a wins server running or have all the routing manually entered into the routing table.  The likelyhood is that your company uses a WINS server, and that you will need to point to that to be able to see the shares.  Also, if your company uses a DNS server I would point it to that also.

To manually add the routing I believe that you use the route command.

You really have it nailed there undertakingyou.  At least its my *guess* that setting up WINS is what might fix kc5hwb's issues.  

Destructchaos - you don't have to give up on the home network and call it ms-voodoo.  *chuckle*  I once had the same problem on my home network and (*I guess*) somehow winbind got installed on my machine (surely I have never done such a thing, I guess it wasnt me, I think) and the problem went away.  

That mysterious installation of winbind (still wondering who DID that on my machine - cos I know my corporate IT people can't/don't support me being on linux at all) somehow also made it possible for me to browse shares on my corporate LAN and WAN (some shares are in other countries across oceans, not just across subnets, bridges, routers and vpn's).  At least thats my *guess* that winbind had something to do with it.

At a rough guess, kc5hwb, I think "google was my friend" assisting me to *guess* that the installation and configuration of winbind might help.  You'd not know how to look for the right info tho would you  - I mean, not while you think that plugging the two machines with different IP configurations into the *same wall outlet* makes cross-subnet sharing/routing just work.  

Back to your MS-Voodoo, destructchaos - google for more detailed help, or ask, but installing winbind (its in the repos) and configuring it appropriately (not forgetting to edit /etc/nsswitch etc etc) will allow your PC to act as a WINS server (its no big deal - quick and easy to set up) and then you will be able to browse windows shares across subnets.

At least thats my guess...it solved my similar issue - or should I say "perhaps MAY have solved my similar problem" -  had I ever done anything like this - I *guess*.

---

### Post by tact on 2007-07-10
> **kc5hwb said:**
> I wouldn't know which router those are connecting to for sure, but I have both machines plugged into the same port on the wall.  True, they could still be routed differently, but in reality they shouldn't be.

Forget about them being in the same wall outlet.  Even if you use a cross-over ethernet cable and directly connect two machines together - if one is configured for IP address 20.24.11.140 and the other is 20.24.10.26  they will ping each other but they won't be able to do windows style sharing without a little help.  

Another helpful guess - all of this is nothing to do with the thread subject you chose ("How to authenticate to a windows domain").  Perhaps you wish to edit it to something more accurate to attract more and more helpful readers.  

Try "How do I browse windows shares across subnets".  Or google for the same.

---

### Post by kc5hwb on 2007-07-13
> **tact said:**
> 
At a rough guess, kc5hwb, I think "google was my friend" assisting me to *guess* that the installation and configuration of winbind might help.  You'd not know how to look for the right info tho would you  - I mean, not while you think that plugging the two machines with different IP configurations into the *same wall outlet* makes cross-subnet sharing/routing just work.  


Been there, done that.  AND... google suggested that I try and "authenticate to a windows domain" hence why I chose that title.

I didn't say anything about plugging them in would make it  work... I simply answered a question about whether they were on the same router, which I do not know.  What I do know is... when I had my XP laptop plugged into this same port, it would at least pull up a login box and allow me to enter my username and password for the domain to access the shared folder.  I can SEE that same folder from my Ubuntu box, but it never *prompts* me to authenticate to the domain my company is on, so it comes up with a msg that says "all items might not be visible" and in reality NO items are visible.  It seems to be seeing the shared folder, but nothing in it.

I am sorry, I was under the impression that this was the "Absolute Beginners Forum" since it is titled that way on the front page.  Perhaps I should better think of it as "if you ask beginner questions, be prepared for smart-azz comments and very few people who really want to help"

Anyway, back to the real problem, calling it "authenticating to a windows domain" or "How do I browse windows shares across subnets", I was also told by someone here that I should try WinBind.  No, my company doesn't use WINS, so that is out.  I will try WinBind now and see if that works

---

### Post by destructchaos on 2007-07-13
> **kc5hwb said:**
> I am sorry, I was under the impression that this was the "Absolute Beginners Forum" since it is titled that way on the front page.  Perhaps I should better think of it as "if you ask beginner questions, be prepared for smart-azz comments and very few people who really want to help"

<sarcasm>you must be new here.  welcome to the internet.  this is a forum, where thousands of people gather to make fun of each other under the pretense of helping others.  enjoy your stay and don't let the fourteen-year-olds who think they are perfect and know everything get to you too much.</sarcasm>

as to your actual problem, there is a "Networking & Wireless" section.  you may want to consider posting a full description of your problem there.

---

### Post by kc5hwb on 2007-07-13
> **destructchaos said:**
> <sarcasm>you must be new here.  welcome to the internet.  this is a forum, where thousands of people gather to make fun of each other under the pretense of helping others.  enjoy your stay and don't let the fourteen-year-olds who think they are perfect and know everything get to you too much.</sarcasm>


ROFLMAO!!  :lolflag:

---

### Post by kc5hwb on 2007-07-13
This may be a simpler problem than what I first thought.  I have Virtualbox installed on this laptop with XP running in the VM session.  I shared out the entire "Cdrive" in the VM and when I go to Places->Network in Ubuntu, that virtual share drive shows up there.  However, when I click on that drive, I get the EXACT same error msg... it opens the folder and says "could not display all contents" but really it doesn't display anything at all.

I have Samba installed... I followed the instructions here -->
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

These are the same instructions I used to install Samba on my Ubuntu desktop at home and it can see all my XP machines at home just fine.  So I don't know if perhaps I messed something up on the installation of Samba on this laptop or if I need to do something more.

---

### Post by tact on 2007-07-14
In your winXP VM what is the iP address?

What is the host machine address?

IF -  you are using a 255.255.255.0 netmask and 
IF - both the above IP addresses are not the using the same on subnet then

guaranteed same problem. 
As I previously suggested - Windows file sharig (or smb) across different subnets is the issue.
As I previously suggested a more appropriate topic title is as above.
As I  previously suggested - a solution.

example of two machines on the SAME subnet  (with 255.255.255.0 subnet mask)
10.20.4.54
10.20.4.23

example of two machines NOT on the same subnet (with 255.255.255.0 subnet mask)
10.20.4.54
10.20.5.23


Also as I previously suggested - need to give more info (and/or a more accurate topic) for better help.  otherwiae anyone trying to help is  just playing 1000 guesses again.

What information?
In any network problem, the very least is the IP addresses of both machines and netmask.  (this time - of the VM and host)

You mention not having the problem on your home LAN:
Check the IP addresses of the machines on your home network - all on same subnet?  And no problem?  Hmmmm.... ?

regards.

---

