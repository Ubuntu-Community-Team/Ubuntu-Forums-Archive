---
title: "Networking with Windows XP PC's"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by steve-shinn on 2007-05-03
Hi,

Installed ubuntu 7.04 64 bit on a spare pc, wired it to my router .... hey presto....I can connect to my home network & see / access the 2 other windows XP based pc's. However, the 2 windows XP based pc's can not view/see see the Ubuntu pc on the network.
Do I need to change some XP settings or Ubuntu settings ?? if so what ??

---

### Post by steve-shinn on 2007-05-03
....bump

---

### Post by leecou on 2007-05-03
I'm sort of having the same problem.

Have you pinged the Ubuntu machine from the xp machine and vice versa?

I can ping each other but can't share the internet connection

L

---

### Post by steve-shinn on 2007-05-03
Yep .... I can ping each of the pc's and every pc can access the internet ..... just cant see the ubuntu pc on the windows network

---

### Post by gh0st on 2007-05-03
You probably need Samba to share files and printers from Ubuntu to your Windows machines. Samba is the Linux file server component. Ubuntu comes with tools to read SMB (windows) shares installed by default which explains why you can read other shares, it doesn't install the sharing components by default though, you have enable it.

It's pretty easy in Feisty. Try the following.

1. Go to System / Administration / Sharing Folders on the main Gnome menu

2. It will prompt you to install the sharing services if you don't have them, just accept. It will download and install some packages. Might take a minute or two

3. Click the General Properties tab and enter the name of your Windows workgroup.

4. Setup the folders you want to share by just adding them on the "shared folders" tab. Make sure you've selected "share though Windows network" and set the "read only" checkbox how you want it. 

That should do it. You should now be able to find your Ubuntu machine n the network neighborhood on Windows.

Hope that helps, good luck :)

---

### Post by gh0st on 2007-05-03
Check this site out for more information - [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

There are loads of good guides about for setting up Samba. Thats a good site generally for problems with Ubuntu actually, might be worth a bookmark, it's not Official though and these Forums are also a great source.

Good luck anyway :)

---

### Post by steve-shinn on 2007-05-03
Do i need to tick the "this computer is a WINS server" on the general tab ?

---

### Post by rafaelperrone on 2007-05-03
gh0st,
I did this exactly and I can see my linux desktop from win xp, but, when I click on it to see my shared files, it asks for a username and password. Ive tried my linux username and pw but it doesnt work. Whi username i have to use or how can I make it available whitout username and pw

Thanks,



> **gh0st said:**
> You probably need Samba to share files and printers from Ubuntu to your Windows machines. Samba is the Linux file server component. Ubuntu comes with tools to read SMB (windows) shares installed by default which explains why you can read other shares, it doesn't install the sharing components by default though, you have enable it.

It's pretty easy in Feisty. Try the following.

1. Go to System / Administration / Sharing Folders on the main Gnome menu

2. It will prompt you to install the sharing services if you don't have them, just accept. It will download and install some packages. Might take a minute or two

3. Click the General Properties tab and enter the name of your Windows workgroup.

4. Setup the folders you want to share by just adding them on the "shared folders" tab. Make sure you've selected "share though Windows network" and set the "read only" checkbox how you want it. 

That should do it. You should now be able to find your Ubuntu machine n the network neighborhood on Windows.

Hope that helps, good luck :)

---

### Post by gh0st on 2007-05-03
You shouldn't need the WINS server no. Sorry I think I forgot to mention that ;)

As for the permissions thing, It could be because you need to setup a Samba user account.

Have a look at this: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_home_folders_with_read.2Fwrite_permissions_.28Authentication.3DYes.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_home_folders_with_read.2Fwrite_permissions_.28Authentication.3DYes.29)

There are a few guides on that site for different types of setup. I found I had to add a user in Samba and then I could use them to login to my shares from Windows. I don't have them set for no login so I'm not totally sure about that sorry, there is a guide on that site though I think. I have my username and password the same on my Windows machine as my Ubuntu machine. That way it seems to login automatically and I still have some security.

Have a look at this for adding and managing network users: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add.2Fedit.2Fdelete_network_users](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add.2Fedit.2Fdelete_network_users)

Samba can be tricky but it's easier once you've done it the first time, like many things in life :)

Good luck

---

### Post by regomodo on 2007-05-03
> **rafaelperrone said:**
> gh0st,
I did this exactly and I can see my linux desktop from win xp, but, when I click on it to see my shared files, it asks for a username and password. Ive tried my linux username and pw but it doesnt work. Whi username i have to use or how can I make it available whitout username and pw

Thanks,

You cannot use your Ubuntu login name and pass. You have to set up a samba password for a user. It's a pain and i really think it should be an option to pass protect your shared folders or atleast sync the users passwords with samba. You can apparently edit smb.conf to do this but i didn't have much success( read as no success).

I thought i had the link somewhere but can't find it. Look around on how to create a samba password

---

### Post by steve-shinn on 2007-05-03
I'm puzzled.....on the link above 2 lines of the instruction reads :-

          o Insert the following line into the new file 

system_username = "network username"

if my user name is steve do I therefore type :-

steve = "networkusername"                with quotations or without ?

or do I type :-

steve = "steve" ???

---

### Post by regomodo on 2007-05-03
sorry. can't help. I didn't use that above guide. It took about 2 commands in the terminal

---

### Post by gh0st on 2007-05-04
Sorry I fell asleep last night, how are you getting on? Do you have the same problem now? You can see the share but not connect to it with a username and password?

If so, you can probably fix it by just adding a user to Samba so you can login. I think in the case of the example in that link you would put "steve" or whatever name you login to Ubuntu with as the "network username".

I think you only need to use these 2 terminal commands. I didn't do the bit where you edit the file when I did my setup and it worked. I only found that guide after I'd already done my system. Try this.

To add a user

```

sudo smbpasswd -a steve
```

To enable the user

```

sudo smbpasswd -e steve
```

You should then be able to use the username and password you set with these commands to login to your shares from the network. Have a go and let me know how you get on.

Good luck ;)

---

### Post by alamandrax on 2007-05-04
setting up the samba password worked. :)

thanks a lot!

---

### Post by gh0st on 2007-05-04
> **alamandrax said:**
> setting up the samba password worked. :)

thanks a lot!

No problem, glad it worked for you ;)

---

### Post by XTREEM|RAGE on 2007-05-09
i'm sorry to bumb this thread, but it helped me until the user part.
I have my own ubuntu feisty machine and a windows laptop(with no login pass). And when i want to add a user @ samba i only get: 
```
sudo smbpasswd -a jermaine
New SMB password:
Retype new SMB password:
Failed to modify password entry for user jermaine

```

do i need to set a password for my windows laptop or not?

tnx!

---

### Post by gh0st on 2007-05-09
> **XTREEM|RAGE said:**
> i'm sorry to bumb this thread, but it helped me until the user part.
I have my own ubuntu feisty machine and a windows laptop(with no login pass). And when i want to add a user @ samba i only get: 
```
sudo smbpasswd -a jermaine
New SMB password:
Retype new SMB password:
Failed to modify password entry for user jermaine

```

do i need to set a password for my windows laptop or not?

tnx!

Sorry I was slow replying, been away from the PC for a bit today, doesn't happen that often ;)

You shouldn't need to set a password on your Windows box to access the Samba share on your Ubuntu machine. I did the exact same setup yesterday after reinstalling Feisty, I was using an XP laptop to connect. 

It looks as though you can't reset the password for that Samba account (jermaine) for some reason. It must already exist on the machine, Samba accounts are separate from your normal Ubuntu login account so you can create another one called something else with the same command, just change the username to something other than jermaine and see if that works.

When you connect to the share from Windows you should get prompted for a username and password by Samba, you need to enter the ones you created here and it should let you in. It worked for me. I shared the folders in the file browser (on Ubuntu), made sure it was on the same workgroup as the other machines and created a Samba user with those terminal commands. Then I connected to the shares on my Ubuntu desktop from my XP laptop. I had to retry the login a few times but it worked after 2 or 3 goes, I think that was down to a cache problem.

Hope that helps. Have a go and let me know what happens. I'll see if I can sort it out for you :)

Good luck

---

### Post by XTREEM|RAGE on 2007-05-09
tnx it's working now :D

---

### Post by gh0st on 2007-05-09
Cool, glad to hear it. Nice work ;)

---

### Post by Warning on 2007-05-13
hi im having some issues related to this and the issue is with my xp machine logging in, in that it just keeps on popping up with the same loggin screen. :(

heres what i've done so far

[SIZE="1"]> **gh0st said:**
> 
It's pretty easy in Feisty. Try the following.

1. Go to System / Administration / Sharing Folders on the main Gnome menu

2. It will prompt you to install the sharing services if you don't have them, just accept. It will download and install some packages. Might take a minute or two

3. Click the General Properties tab and enter the name of your Windows workgroup.

4. Setup the folders you want to share by just adding them on the "shared folders" tab. Make sure you've selected "share though Windows network" and set the "read only" checkbox how you want it. 

and then

> ```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
gksudo gedit /etc/samba/smb.conf

```
    * Find this line 
```
...
;  security = user
...
```
    * Replace with the following lines 
```
  security = user
  username map = /etc/samba/smbusers

```
    * Find this section 
```

...
# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
  writable = no
...
```
    * Replace with the following lines 
```
# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
  writable = yes
```
    * Save the edited file
    * Read #How to add/edit/delete network users 
```

sudo testparm
sudo /etc/init.d/samba restart
```


and then

> 
```
sudo smbpasswd -a system_username
gksudo gedit /etc/samba/smbusers
```
          o Insert the following line into the new file 
```
system_username = "warning"
```
          o Save the edited file 
    * To edit network user 
```

sudo smbpasswd -a warning

```


and then i enter

```

sudo smbpasswd -e warning

```[/SIZE]

so have i done something wrong? or is it my windows xp machine?

please help

-Warning

---

### Post by gh0st on 2007-05-15
Sorry it took me a while to reply. I've had a look through what you did and it looks ok. I don't think it should be the XP system causing the problem. I didn't do a lot of the things that you've done on your setup. I didn't edit the smb.conf for instance or any of the samba user files.

All I did was the steps I listed and then the 2 terminal commands to add the samba user and enable it. After that  got a prompt for my username and password when I browsed the samba share from Windows. I think maybe you've inadvertently changes something extra that you didn't need to. It's confusing with all the tutorials and stuff. Maybe restore the original smb.conf before you changed it and see if that helps.

Let me know how you get on and if you need any more explicit help don't hesitate to holler, I'll be more attentive to my email I promise ;)

Good luck :)

---

