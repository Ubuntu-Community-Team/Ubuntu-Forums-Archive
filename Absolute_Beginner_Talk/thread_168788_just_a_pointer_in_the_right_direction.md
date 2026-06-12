---
title: "just a pointer in the right direction"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by kriding on 2006-05-01
Hi all,

I've had Ubuntu installed for just under 48 hrs now and must say i am liking it. The install found all my hardware and connected to my router and network (powerline) with absolutly no input from me (that alone beats windows for me :p )

I am slowly finding my way around installing extra apps and things, however, some require me to log into the root account...therein is my problem!

Whenever I try, and i get asked for the password...there isn't one that I'm aware of, I wasn't asked to enter one during the install, so I was wondering if there is a default password that i'm not aware of?

I have tried the manual, but i don't find it (or any manual for that matter) useful at all....i'm not a manual kind person, as I like to go in and break things then figure it out from there.

I have taken the plunge with this distro, (i tried SUSE and Debian last year and hated them) and after 6 hrs on a dual boot system, I am now fully linux, so I will be posting like mad here till I get it right.

Thanks in advance for any advice:)

---

### Post by syg00 on 2006-05-01
Ubuntu doesn't use a root account - if you are asked for a password, it'll be _your_ password. The one you logged in with.
If you are in a console/terminal, and get a "not Authorised" message, add "sudo" (no quotes) to the front of the command. Generally you'll be asked for a password - just your password again.
Think of it giving you root  priviledge - as a surrogate.

---

### Post by kriding on 2006-05-01
thanks...i'll give that a go

---

### Post by gingermark on 2006-05-01
Read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) for the gory details.

---

### Post by tribaal on 2006-05-01
Hehe very simple:

Ubuntu is a sudo distribution. That means you *never* log in as root. Instead, the user you set up at install was granted sudo rights. 

Let's make it simple: If you want to run foobar as root you want to put the word sudo in front of it instead:

*apt-get install foobar*
becomes
*sudo apt-get install foobar*

The system will ask you for a password. This is *your* password, not the root password.

From then on you shouldbe able to do anything with your system ;)

cheers :)

- trib'

**Edit:** Awww too late :)

---

### Post by kriding on 2006-05-01
thanks guys....it's all be really helpful so far...

how do I move a folder from one location to another? I inadvertantly installed skype on my desktop, how do I move it? and how do i change permissions of a folder?

---

### Post by syg00 on 2006-05-03
I stayed out of this as I am a CLI (command level interface) sort of person. I prefer to use a terminal command(s) rather than a GUI.
Linux has a "mv" command - see "man mv" from a terminal. There must be a "drag'n'drop" from nautilus, but I've never used it.
As for permissions/ownership, right mouse-click/permissions should work. Else check the man for chown and chmod - what I use ...   ;)

---

### Post by az on 2006-05-03
[QUOTE=kriding]thanks guys....it's all be really helpful so far...

how do I move a folder from one location to another? I inadvertantly installed skype on my desktop, how do I move it? and how do i change permissions of a folder?[/QUOTE]
Did you install skype as root?

Try to avoid installing things as root, other than using synaptic.

---

### Post by steve.horsley on 2006-05-03
[QUOTE=kriding]thanks guys....it's all be really helpful so far...

how do I move a folder from one location to another? I inadvertantly installed skype on my desktop, how do I move it? and how do i change permissions of a folder?[/QUOTE]

You can use nautilus (the explorer-style file manager that you get from Places->Home Folder) to move files and folders. Either drag between two nautilus windows, or get the filesystem tree in the sidebar and drag from the right-hand pane to a folder in the sidebar.

To change permissions, right-click and choose Permissions. 

You may not have the permissions to do the things you want unless you are doing them within your home directory. You can get a root privilege nautilus window with the command **gksudo nautilus** but be very careful with it because then you have full rights to trash the whole system, and nautilus won't ask "Are you sure you want to trash your system now?" - it'll just do what it's told.

---

### Post by crash469_2u on 2006-05-03
you can activate the root account by using the folowing command outputs in the termanal:

sudo passwd root

it will come up asking for your user password and a new "root password"
 then you will beable to log out of your user account and login as "root" simmalar to the windows login.

---

