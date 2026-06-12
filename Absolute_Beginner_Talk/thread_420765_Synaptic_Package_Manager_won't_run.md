---
title: "Synaptic Package Manager won't run"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by doriard on 2007-04-23
I tried to enable all repositories in Synaptic Package Manager by checking all the boxes on the home tab, then selected "Main" source instead of "US server".  Now the SPM won't run at all!  When I try to start it up, it immediately closes with the error message:

E: Dynamic MMap ran out of room
E: Error occurred while processing libalps1-dev (NewPackage)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I tried purging or removing libalps1-dev, the the same error message occured when it tried to purge it.

How can I get the Synaptics Package Manager  running again?

---

### Post by LaurelLynn on 2007-04-23
Dear doriard,

Try editing /etc/apt/sources.list so that it contains only the basic repositories.  Some thing more like this:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

Those are the ones I rely on.

---

### Post by baekeland on 2007-04-23
Is there a way to change the Sources.List or delete a line in the sources List line 51 to be specific.

Best,

Bill

---

### Post by LaurelLynn on 2007-04-23
Synaptic is a front-end for apt-get.  If you edit the sourcles.list fiile:

$ sudo gedit /etc/apt/sources.list

You can change the repositories it uses.  What I believe is happening, is that when you added the new repository in Synaptic, it put entries in here.  So if you can find the new entries, you can comment them out by putting a ¨#¨ in front of them.

 When you restart Synaptic hit the reload button it will update its package database. That should get you back to normal (if not try other repositories till your down to the defaults).

---

### Post by baekeland on 2007-04-24
Laurel Hi

Bash $: command not found --any other suggestions?  This is the message I get all the time:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 49 in source list /etc/apt/sources.list (dist), E:The list of sources could not be read.'

What I was thinking of doing is to change the name of my current Sources.list to the backup Sources.List and rename the Sources.list giving me problems to Sources.List backup.

I need to edit a line in Sources.List a # would be fine but the text editor absolutely refuses to save any changes telling me I do not have permissions to do so.

Best,

Bill

P.S.  I stole your sources.list you put out there hope you don't mind

---

### Post by LaurelLynn on 2007-04-24
gedit has an option to go straight to a line number. From the menu bar at the top it is Search->Go to Line.

The editor probably won´t save because it did not open as the root user.  Try this command before editing, it will get you to a root prompt:

$  sudo -s

#  gedit /etc/apt/sources.list

That should let you save.  If not then try:

#  ls -l /etc/apt/sources.list

If the permissions look like something like  this :    -r--r--r-

Enter this and try again::

# chmod +w /etc/apt/sources.list

Hit Control-D when you done to leave the root prompt.

Let me know if you are still stuck.

---

### Post by baekeland on 2007-04-24
Laura,

I feel like I'm in The Twilight Zone ... laughing using your commands in Konsole as Root I received no errors just took me back to my prompt thinking the command(s) had changed my permissions I went to sources.List and tried placing the # where it belongs No luck I even tried changing the name from Sources.save and other Sources in the folder trying to get a workable Sources.List before I did what I did to make this mess -- no go -- it refused me not the first time but even OS/2 Warp never refused me ....laughing.  If you can learn OS/2 Warp one can learn ANYTHING ....laughing I actually liked the OS unfortunately IBM killed it -- alas - why do the good things die and WinBlows gets so powerful?

Best,

Bill

---

### Post by baekeland on 2007-04-24
At least somehow the problem line has hopped from the 50's to the 40's -- beats me.  Probably my deleting repositories. Wish I could delete that repository!

Bill

---

### Post by LaurelLynn on 2007-04-24
Whoops,

I should have realized you were using Kubuntu.  Gedit is a Gnome program.  So gedit will be something like kedit (you probably figured that part out).

Note:  Linux is case sensitive so  ¨sources.List¨ won´t work the ¨L¨ has to be lower case. Synaptic is looking for the file which is exactly  ¨sources.list¨ and it has to be in ¨/etc/apt¨.

That controls the repositories.  I would try just a single repository first, nothing in the file but:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse

Another note: I am running 6.06LTS which is ¨dapper¨.  Your version might be ¨edgy¨ or ¨fiesty¨ (maybe even ¨breezy¨).

If it still won´t let you write to the file, I would try writing to a temporary file ¨temp¨, then using the move command ¨mv¨ to swap files:

$ sudo -s
# mv /etc/apt/sources.list  /etc/apt/source.list.bak
# mv temp  /etc/apt/sources.list

---

### Post by doriard on 2007-04-24
I will diverge back to the original post question for a moment.  It turns out that I did have sources.list backed up, I just didn't remember where to find the file -- I've been working with Linux for a whole 2 days.  Anyway, the interesting part is that before this problem, I was haven't trouble finding the 2.5 version of libc6-dev, which I needed in order to install the nvidia drivers.  Well, after restoring sources.list, I unchecked all of the repositories, restarted Synaptic, then added back the repositories one at a time until all were checked again. Now, the most recent version of libc6-dev showed up for me to install!  I will have to remember that for the future -- to force the repositories to update, just uncheck all of them, restart, and check them again.  I had clicked on the refresh button numberous times, but it never fully update until I did this.  I should post this in a separate message so that others can see it.

Now, on the the next problem.
I did get the nvidia drivers installed using Nvidia's method of installing "sh nvidiafilescriptname.run" from root.  However, when I rebooted (the nvidia splash screen showed), after I logged in, the whole display went orange, with nothing else showing.  I can't do anything.  Next step -- should I restore the nvidia-xconfig file that was backed up?  Where is it located?

Thanks.  Without these forums, setting up Ubuntu would be impossible.

---

### Post by LaurelLynn on 2007-04-24
I'm glad you have your repositories sorted out!

As to nvidia, I don't have a system with one of their cards (yet) so I don't know the details of installing its drivers.

I do know there are a **whole lot** of threads on the forum about them. So putting "ubnutu nvidia" into any search engine should turn up quite a few threads.

Or, you could start a new thread since basically you have a new problem, and it needs a new title to be seen by those with the right knowledge.

Good Luck!

---

