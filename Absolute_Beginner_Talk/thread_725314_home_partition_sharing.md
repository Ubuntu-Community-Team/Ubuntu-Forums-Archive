---
title: "/home partition sharing"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-03-15
I'm planning on installing opengeu (a fork of ubuntu with the enlightenment wm and other things) and was wonderging whether it would be fine to share the same home partition with ubuntu? I know that with other distros there could be conflicting configurations, but since this is basically ubuntu in different clothing, would it still be a problem?

the opengeu home page: [http://opengeu.intilinux.com/Home.html](http://opengeu.intilinux.com/Home.html)

---

### Post by atoc on 2008-03-15
No problem. 
I've installed the variations of Ubuntu and other distros all using a dedicated seperate /home partition.
That's the whole point of the installers recommending a seperate home partition - change your flavor, keep your contents :)
One advantage - in several cases, if you choose the same window manager - your toolbars and settings are exactly the same \m/

---

### Post by prshah on 2008-03-15
> **intense.ego said:**
> I'm planning on installing opengeu (a fork of ubuntu with the enlightenment wm and other things) and was wonderging whether it would be fine to share the same home partition with ubuntu? I know that with other distros there could be conflicting configurations, but since this is basically ubuntu in different clothing, would it still be a problem?

the opengeu home page: [http://opengeu.intilinux.com/Home.html](http://opengeu.intilinux.com/Home.html)

The only problem with shared home partition is to ensure that your UIDs (user IDS) and GUIDs (group IDs) match. 

Check your /etc/passwd and make a  note of your UID and then from the /etc/group make a  note of the GUID for the users you will create on both systems.

UID and GUID are the third column in of the files mentioned above.

Now install your opengeu OS, but do not login as the ubuntu user. Create some other username.

Log in with the other username, then create a user with your ubuntu username. Dont login with that user yet.

Open the above files, change (if necessary) the UID and GUID to match.

Recursively change ownership for all files in your ubuntu username's home directory. Eg:
```
sudo chown -R [ubuntuusername]:[ubuntuusername] /home/[ubuntuusername]/ 
```

You can now login with your ubuntu username and see if everything is OK.

CAVEAT:
I have NEVER shared a "/home" partition since I have only one linux OS installed. This was something that I had read up about a while ago. Please consider researching more and taking a proper backup before doing anything like this.

---

### Post by kellemes on 2008-03-15
> **prshah said:**
> 
I have NEVER shared a "/home" partition since I have only one linux OS installed. This was something that I had read up about a while ago. Please consider researching more and taking a proper backup before doing anything like this.

+1 for the advice.
I always run dual-boot, currently even triple-boot but never shared /home either.. at best it'll work. Most of us can spare a little space for a /home-partition.. or two.
If crap happens with /home you kill 2 distro's really..

Edit: By the way.. I currently have opengeu running in a vm and it looks great.

---

### Post by intense.ego on 2008-03-15
> **prshah said:**
> The only problem with shared home partition is to ensure that your UIDs (user IDS) and GUIDs (group IDs) match. 

Check your /etc/passwd and make a  note of your UID and then from the /etc/group make a  note of the GUID for the users you will create on both systems.

UID and GUID are the third column in of the files mentioned above.

Now install your opengeu OS, but do not login as the ubuntu user. Create some other username.

Log in with the other username, then create a user with your ubuntu username. Dont login with that user yet.

Open the above files, change (if necessary) the UID and GUID to match.

Recursively change ownership for all files in your ubuntu username's home directory. Eg:
```
sudo chown -R [ubuntuusername]:[ubuntuusername] /home/[ubuntuusername]/ 
```

You can now login with your ubuntu username and see if everything is OK.

CAVEAT:
I have NEVER shared a "/home" partition since I have only one linux OS installed. This was something that I had read up about a while ago. Please consider researching more and taking a proper backup before doing anything like this.

Why can't the first username I create, just be the same as the one in the Ubuntu install? Or is it because the GUID is uncertain?

BTW: I like  your sig ;)

---

### Post by intense.ego on 2008-03-16
anyone?

---

### Post by prshah on 2008-03-16
> **intense.ego said:**
> Why can't the first username I create, just be the same as the one in the Ubuntu install? Or is it because the GUID is uncertain?

BTW: I like  your sig ;)

Thanks for the compliment; it took me just 90 days to figure out a good sig.

I suggested that you dont have the same name initially because if you DO keep the same name, and login with that name before changing the UID and GID and updating your /home partition, I fear that you WILL kill it and me along with it for offering advice in the first place.

---

### Post by intense.ego on 2008-03-17
bump. anything else I need to know?

---

### Post by intense.ego on 2008-03-19
*bump*

---

