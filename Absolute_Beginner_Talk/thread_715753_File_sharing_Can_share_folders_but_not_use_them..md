---
title: "File sharing: Can share folders but not use them."
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by NeonSamurai on 2008-03-05
Hi,

I'm running a Gutsy server over a small network and I'm trying to setup file sharing.

Basically I've created a folder that I want to give people access to and installed samba, listed it as a shared folder and can find it over the network on MS and Linux machines. However, I can't create, add or import and new files into that directory (I get a message reading: "You do not have permissions to write to the destination."). 

I've used chown to change the owner rights but the problem persists.

How can I change the folder to give everyone access to it over the network?

Thanks


Mark

---

### Post by opositive on 2008-03-05
Are you looking to have your users authenticate to the file share or do you want to use it like a basic Windows file share.  Meaning that it would be globally readable/writable on the network for anyone on your network without having to provide a username/password.

Also, if you can, post or attach your /etc/samba/smb.conf file so I can confirm your settings and give you a usable configuration.

---

### Post by NeonSamurai on 2008-03-06
Hi oposite,

Your post set me in the right direction. Essentially my smb.conf file had this to say concerning my files:

> [share]
path = /home/share
available = yes
browsable = yes
public = yes
writable = no


I was trying to create/copy files to the share directory, so I amended the *.conf file accordingly (writable = yes). 

I also used [chmod]("http://www.ss64.com/bash/chmod.html") to give the command $ sudo chmod 777 /home/share , which means that universal access has been granted to this folder. 

Cheers for pointing me in teh right direction.


Mark

---

### Post by hyper_ch on 2008-03-06
```

writable = no 

```

Well, what could that mean?

---

### Post by Mauler5858 on 2008-03-06
Change the writable=no line to allow your attached machines to write/edit items in the folder.

---

### Post by opositive on 2008-03-06
You had mentioned to me you would be interested in a solution as follows.

Here is an example of setting up two shares to be accessed by different groups of users.  One for linux and one for windows... (I don't know if this is the best way, but it has worked for me.)

1. Create a new group admin level group to own the shares named "samba" and add your user account to the member list.

2. Create a new user account named "linshare".  I would suggest making this user unprivileged as it will only be used for accessing file shares.  Also, set the shell to /bin/false so the user won't be able to log into the system interactively.

3. Create a new user account named "winshare".  I would suggest making this user unprivileged as it will only be used for accessing file shares.  Also, set the shell to /bin/false so the user won't be able to log into the system interactively.

4. Set a samba password for each user: sudo smbpasswd -a [user]
    - You will be prompted to provide the password.

5. Create directories where the shares will be pointed.
    sudo mkdir /var/shared /var/shared/linux /var/shared/windows

6. Set ownership and permissions on the directories.  This will allow the share user to own all items along with the "samba" admin group.  The chmod g+s will ensure any files will inherit the "samba" group ownership.
    sudo chown -R linshare.samba /var/shared/linux
    sudo chown -R winshare.samba /var/shared/windows
    sudo chmod -R 770 /var/shared/linux /var/shared/windows
    sudo chmod g+s /var/shared/linux /var/shared/windows

7. Define the shares in your smb.conf file.

[win_share]
        comment = Windows Users
        path = /var/shared/windows
        browseable = yes
        read only = no
        guest ok = no
        valid users = winshare
        create mask = 0770

[lin_share]
        comment = Linux Users
        path = /var/shared/linux
        browseable = yes
        read only = no
        guest ok = no
        valid users = linshare
        create mask = 0770

8. Restart your samba services and give it a try.  
    sudo /etc/init.d/samba restart

---

### Post by NeonSamurai on 2008-03-06
Superb oposite, just what I was after, all the relevant details in the same place.

I'll give this a try and see how I get on.

---

### Post by NeonSamurai on 2008-03-07
Superb!

I've amended your instructions accordingly and am now sharing files across my network.

Thanks again Oposite

---

### Post by NeonSamurai on 2008-03-07
Okay, another question:

Supposing I wanted to give the user '**linshare**' access to the **windows** folder as well as the** linux** one what would I need to do?

---

### Post by opositive on 2008-03-07
You could add the linshare user to the valid user list of the windows share and add linshare to the samba group.  linshare would then have full access to both shares.  The only issue then would be that if linshare created a file in the windows share I don't think the winshare user would be able to access it.

Let me review the solution based on this new requirement.

---

### Post by NeonSamurai on 2008-03-07
Thanks.

So would the valid user list be here in the *.conf file:

> [winshare]
comment = Windows Users
path = /home/vault/windows
browseable = yes
read only = no
guest ok = no
[COLOR="Orange"]**valid users = winshare**[/COLOR]
create mask = 0770


And if so, how do I add extra users? Is it just a case of adding them onto the list. i.e:

valid users = winshare linshare root user

---

### Post by opositive on 2008-03-07
Yes, you would add each user name to the valid users line separated by a space.

---

