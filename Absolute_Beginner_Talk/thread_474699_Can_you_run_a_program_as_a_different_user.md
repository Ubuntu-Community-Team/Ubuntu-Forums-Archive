---
title: "Can you run a program as a different user?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Bou on 2007-06-15
Let's suppose my girlfriend wants to run Rhythmbox using her settings and library, but I don't want to close my session. Is it possible to let her run it through "su"?

I tried the following:

> david@david-laptop:~$ su susana rhythmbox
Password: 
/usr/bin/rhythmbox: /usr/bin/rhythmbox: cannot execute binary file

I also tried:

> david@david-laptop:~$ su susana
Password: 
cristina@david-laptop:/home/david$ rhythmbox
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

cannot open display: 
Run 'rhythmbox --help' to see a full list of available command line options.cristina@david-laptop:/home/david$

Anything I'm missing? thanks in advance.

---

### Post by capitalistpiglet on 2007-06-15
you may need to add the user to the x server access list.
```

sudo xhost +local:username

```
If that doesnt work then you might be able to do it with this
```

ssh -X susana@localhost

```
Then running the application. Although you will need ssh installed.

---

### Post by nitro_n2o on 2007-06-15
you might wanna check out 'klog' which works fine on AFS

---

### Post by Bou on 2007-06-15
> **capitalistpiglet said:**
> you may need to add the user to the x server access list.

What I did was use "sux" &#8594; sux is a wrapper around the standard su command which will transfer
your X credentials to the target user.

now if I type:

> david@david-laptop:~$ sux susana
Password: 
susana@david-laptop:/home/david$ rhythmbox

or even if I type:

> david@david-laptop:~$ sux susana rhythmbox

Rhythmbox opens just fine, and using her options. But, is there any way to make sux ask for a password graphically? so I can just add a launcher for her and forget the whole thing.








EDIT: By the way, "sudo xhost +local:susana" worked... more or less. I can type "sudo rhythmbox susana" to launch the program, but there is no way to make it ask for the pass graphically.

---

### Post by Blippe on 2007-09-14
> **Bou said:**
> What I did was use "sux" &#8594; sux is a wrapper around the standard EDIT: By the way, "sudo xhost +local:susana" worked... more or less. I can type "sudo rhythmbox susana" to launch the program, but there is no way to make it ask for the pass graphically.

gksudo -u susana rhythmbox

---

### Post by jerstew on 2007-09-27
I like to use Thunderbird to access my email, but I like it to be private from others using my computer. So, I have a separate account for that.

First add that user to xhosts list:
xhost +*user*
or
xhost +localhost:*user*

Then setup a launcher on the Desktop, first by dragging the application from the app menu to the Desktop. Second, edit the launcher. Right click -> Properties -> Launcher Tab

Edit command to look like this:
gksu -u *user* mozilla-thunderbird

This will bring up a dialog asking for the password. Of course, once the launcher has been used, your username will be added with a timestamp to sudoers, and the launcher won't require a password for 15 minutes. the sudo/su commands have options to disable this, gksu does not.

You can even get fancy and change the default message on the gksu dialog with the -m option
gksu -m "Stay out of my email" -u *user* mozilla-thunderbird

Hope this helps you or somebody.

---

### Post by lucianindianapolis on 2007-12-02
jerstew, in response to the sudoers timestamp. . . that is easily changed by going to the terminal and typing: 

export EDITOR=gedit && sudo visudo

When gEdit comes up, look for a line similiar to this:

```
Defaults:username timestamp_timeout=2
```

If that line isn't there, simply add it and replace username with your login name. the 2 in timestamp_timeout=2 is equal to minutes and 0 means it will ask everytime, less than 0 it will never ask once its been entered.

---

### Post by MastroOmbroj on 2007-12-27
> **jerstew said:**
> First add that user to xhosts list:
xhost +*user*
or
xhost +localhost:*user*



Does not work for me. I got errors:

> ~$ xhost +user2
xhost:  bad hostname "user2"

~$ xhost +localhost:user2
xhost: unknown address family "localhost"
xhost:  bad hostname "localhost:user2"

After:
> ~$ xhost **+local:***type-here-whatever-you-want*
non-network local connections being added to access control list
My user2 can connect to XServer. So I can run programs via gksudo. But now any local user can connect to X, not only user2.

Any idea how can I allow to execute apps as another user in my login session without adding all local users for that?

**Update:** solution found [here]("http://archive.netbsd.se/?ml=xwin-discuss&a=2007-02&t=3073511"):
> $ xhost +si:localuser:user
Now my temp user can't run programs. And user2 can.

---

