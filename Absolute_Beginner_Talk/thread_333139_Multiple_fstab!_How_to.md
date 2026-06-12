---
title: "Multiple fstab! How to?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-01-07
Ok so at home I have a server machine setup and it's /home dir is shared using NFS with all the other machines in my house. So the effect is that whatever machine any person logons they get the same setting and files etc.

Now with my laptop what I did was installed ubuntu on it twice where one was setup to use the shared /home dir and the other had its own. This way I can use my laptop away from my home network.

But now I have to install/update things on both instalations and though this was just plain dumb because the only thing that is differnet is the good old /etc/fstab file.

So I was thinking maybe I could do somthing to get grub to make ubuntu use a differnet /etc/fstab file? one where it mounts the NFS share and one that mounts a partition.

Anyone got any ideas?

---

### Post by guysmiley25 on 2007-01-08
Bump

---

### Post by mahy on 2007-01-08
IMHO, one system == one fstab. there's a one-one relationship. In other words, you're out of luck.

---

### Post by guysmiley25 on 2007-01-08
Yes that is my problem. But does anyone know how I could get the effect I am after?

---

### Post by guysmiley25 on 2007-02-09
Bump!

I thought about making a script that could replace the fstab file.

Eg

```

rm /etc/fstab
cp /etc/fstab.local /etc/fstab
mount -a
startxfce4

```

and 

```

rm /etc/fstab
cp /etc/fstab.network /etc/fstab
mount -a
startxfce4

```

And the maybe having a local.desktop and a network.desktop in the "/usr/share/xsessions" directory that points to those scripts.

But I have a problem, because those commands get ran as the user that is logging in!

Any one, any help on this will be really good!

Thanks

---

### Post by guysmiley25 on 2007-02-10
Bump!

---

### Post by po0f on 2007-02-10
guysmiley25,

Instead of mounting the home directory over NFS on the laptop, why don't you use rsync to keep the contents in sync with the server's?  When you want to take the laptop with you, rsync from the server to your laptop.  When you get back home, rsync the files back to the server.

---

### Post by shareMenaPeace on 2007-02-10
You need somekind of a script which ejects the file on click.

Search for script or bash? script or something ...

---

### Post by guysmiley25 on 2007-02-10
Cheers po0f .

But the reason I do not want to sync is because in my home directory I have over 200 gb of information!!! And also for when I'm away from my home network I want to have different settings. However even if I get my desired effect I will want to sync some files still.

So this being the case I think your right and the soln will be to sync. So what tools and command will I need?

I will want to sync certain files/directory's.  eg

/home/guysmiley/.ssh
/home/guysmiley/Music

etc.

Thanks heaps!

---

### Post by guysmiley25 on 2007-02-13
Ok so I found away to do what I want sort of

```

#!/bin/bash

rsync -arvu /remote/guysmiley/.amsn ~
rsync -arvu /remote/guysmiley/.bluej ~
rsync -arvu /remote/guysmiley/.cache ~
rsync -arvu /remote/guysmiley/.config ~
rsync -arvu /remote/guysmiley/.googleearth ~
rsync -arvu /remote/guysmiley/.gqview ~
rsync -arvu /remote/guysmiley/.local ~
rsync -arvu /remote/guysmiley/.mozilla ~
rsync -arvu /remote/guysmiley/.mozilla-thunderbird ~
rsync -arvu /remote/guysmiley/.mythtv ~
rsync -arvu /remote/guysmiley/.xmms ~
rsync -arvu /remote/guysmiley/.xscreensaver ~
rsync -arvu /remote/guysmiley/Miscellaneous ~
rsync -arvu "/remote/guysmiley/My Movies" ~
rsync -arvu "/remote/guysmiley/My Pictures" ~
rsync -arvu "/remote/guysmiley/Projects" ~

```

Where in the fstab I have my NFS setup to mounted at /remote.

But what I would rather do is have rsync do
```
rsync -arvu /remote/guysmiley /home
```
But exclude some files/dir.

Any ideas?

---

### Post by quartic on 2007-03-12
I believe what you are looking for is:

```
   rsync -arvu --exclude-from=FILE  /remote/guysmiley /home 
```

Where FILE is a filename that contains patterns of filenames to exclude. (see 'man rsync' under  'FILTER RULES' for more information).  Basically the file will be a list of filenames that you want to ignore.

A file containing the following: 
```

foo
bar* 
```

would cause the file 'foo' and all files that begin with 'bar' to be ignored on the rsync.

---

### Post by guysmiley25 on 2007-03-13
Thanks quartic that was very helpful.

I'm looking though the man now. But you got me on the right path.

Currently I do not quite understand rsync or what the options I'm using are for. Hopefully I'll pick it up.

However for the mean time I have another problem. I used the same command to synchronize my mp3 player. But does not do quite what I want and I want to know if what I want to do is possible.

I want to synchronize /home/shared/Music with /media/IAUDIO/Music

First of all I want to ignore ape file. eg Song.ape as my player can only play flac, wav, mp3, ogg. I'm guessing that --exclude-from=list.txt where list.txt contains the line (*.ape).

Second, say if I rename a file in /home/shared/Music. eg Song1.flac to Song01.flac. When I run the synchronize again. I do not want to end up with both Song1.flac and Song01.flac in /media/IAUDIO.

Is rsync smart enough to rename the file or will it delete it and copy over the other one.

Thanks.

---

### Post by Mr. C. on 2007-03-13
Write yourself a startup script that runs just after the network is brought up, interrogates the IP address if your NIC and switches /etc/fstab based on that.

This is pretty trivial.

MrC

---

### Post by guysmiley25 on 2007-03-13
So this can be done? This would be so much better!

So these are the steps I need to do:

1. Write a script that
- Checks to see if I'm plugged into my network.
- Swaps the fstab file accordingly.

2 Set the script to run after the network is bought up but before fstab is set?

Is this correct? I think writing the script would be easy enough. But setting it to run at that moment I would have no idea how to do!

As for the script are you suggesting that I check the IP for the condition. I'm not sure about this as I will plug into other networks time to time and there is a chance that the IP is the same. Maybe a better condition would be to check for a file that I will create and store on my network somewhere. However can I check for the existence of such a file at this point in the startup?


As your synchronizing my mp3 player I have come up with this:
```
rsync -arvu --exclude=*.ape  /home/shared/Music /media/IAUDIO
```

This is all good however the second time I ran this command to see what would happen it took a long time to go though. And I was thinking why not just write a script that would delete the remote files and then copy over the local files? Would it not be faster. The reason I thought of synchronizing is because I thought it would be faster because I would only need to copy over the files that did not exist on the mp3 player. And therefore would take almost no time at all if no or little files needed to be transfered? Is this not the idea? Am I missing the point to synchronizing? Is what I want to do achievable?

Any ideas would be awesome.

Thanks guys.

---

### Post by Mr. C. on 2007-03-13
The network starts up with the script /etc/rcS.d/S40networking.  The rcN.d scripts are a series of scripts that run in numeric order at the various run levels.  You want your script to run after the S40networking script, but before the S45waitnfs script

S35mountall.sh
S40networking
S45waitnfs.sh

There is a little catch with Ubuntu network that you need to be aware of.  The S35mountall.sh script actually tries to mount the NFS file systems even before networking is up.  The nfs mounts will go into the background and wait for the network to come up.  This waiting happens with S45waitnfs.sh.  It would probably be easiest to change the fstab before S35mountall.sh (easiest) to not include your home nfsmounts, and do the nfs mount yourself after the S40networking.sh script after your placed your nfs home mount fstab in place.

I would have just one fstab that had no auto nfs mounts in place at boot, and then just have a script that mounts all nfs file systems after checking the IP.  That way you have one fstab, and have control over when to mount nfs file systems.

As for what you use to check if you are on your home network, you could use any of a number of things.  pinging your server, domain name from your router; its up to you.

Hope this helps,
MrC

---

### Post by guysmiley25 on 2007-03-13
So would I have something like this:

S35mountall.sh
S40networking
S41networkcheck.sh
S45waitnfs.sh

And in networkcheck.sh have something like:

```

if [ network ]

then
    mount -t nfs 10.1.1.1:/home /home
else
    mount -t ext3 /dev/hda2 /home
fi

```

And in my fstab have no entries for /home.

Now while I'm here I'll ask how I can check that a IP exist and have it returned as a boolean true or false. I have done a little programing and scripting in the past but I'm only just starting to get used to scripting in Linux.

Thanks MrC.

**[COLOR="Red"]Edit:[/COLOR]** One more thing I also have a S43portmap file in /etc/rcS.d.

---

### Post by Mr. C. on 2007-03-13
You can add both NFS and /home entries into your fstab.  Just make them noauto entries.  That way, they are defined there, and you just use:

mount  /dev/hda2 /home
mount 10.1.1.1:/home

and mount will look in the fstab table for the correct entry.

ipconfig eth0 will give you information about your eth0 interface.  You'll have to decide what you want to look for, to determine if you are on your home net or elsewhere.  But here's a quick check for the IP address, and easy for you to follow:

```
ifconfig eth0 | grep addr: | grep -q 10.1.1.1
if [ $? = 0 ] ; then
   echo "network is 10.1.1.1"
else
    echo "network is remote"
fi

```
portmap is required for NFS.

MrC

---

### Post by guysmiley25 on 2007-03-14
Thank you so much MrC that has done the trick.

I would just like to understand somethings about the process.

ifconfig eth0 | grep addr: | grep -q 10.1.1.1

Returns a sting if I'm connected to the 10.1.1.1 network


Then as the condition we used $? = 0. Does $? hold the last piece of output? I notice that grep -q just makes the output not displayed in the terminal?

Also does $? = 0 Test for an empty string? Maybe I'm getting this all wrong!


Something else I was wondering about is if /etc/rcS.d is the location for startup processes, then what about shutdown processes?



Now I want to implement one more thing. In the condition that I'm not connected to my network I want to check to see if I have Internet access and if so then setup a ssh tunnel and mount some nfs shares via the tunnel or mount sshfs.

eg
```

if [ network ]
then
    mount 10.1.1.1/home
else
    mount /dev/hdb2 /home
    if [ internet ]
    then
        ssh me@mydomain -L:1213:10.1.1.1:1213
        mount remote:/shared /shared
    fi 
fi
exit

```

However when you run the command "ssh me@mydomain -L:1213:10.1.1.1:1213" you get asked for a password. and then get the terminal for mydomain. But a more important question is. Can sshing be done at this point in the process? Also is nfs mounting just a matter of forwarding the correct port. If so what port is this?

Any help or ideas on this would be fantastic.

---

### Post by Mr. C. on 2007-03-14
That's excellent.  Nice work.

The $? variable is the shell's variable to report the exit code of a prior command.  It is always an integer, not a string.  In a pipeline, $? represents the exit code of the last command that ran.  In this case, it was the grep, which ran silently (-v) and was only used to test if the IP address was found.

The test command, abbreviated as "[" and "]" tested the return code from grep.  0 = success, non-zero = failure.

Here's some explanations of the SYS V unix init scripts.  Read week 2 notes regarding :"Boot & Shutdown / The Super User - root" at : [http://cis68c1.mikecappella.com/calendar.php](http://cis68c1.mikecappella.com/calendar.php)

I wouldn't recommend doing your network check/ssh connect/shared fs in a startup script, as you'll find plenty of times where you have a connection, but it is weak, or flakey, and you'll be hanging part of the boot process.  This type of thing would be better left to your first login, as in a .bashrc or .login (depending up shell), or even making yourself a bash function and just call it when you want it.  If it is mounting your home directory, you have to do this before you login, so the method I'm suggesting wouldn't work.  NFS over SSH on a slow or problematic link will not be an exciting experience.  Beware.

See if this helps / makes sense.

MrC

---

### Post by guysmiley25 on 2007-03-14
I agree that mounting a home dir via ssh/nfs, would not be ideal. And that mounting any filesystem via ssh/nfs in the boot process would slow down the boot process. So I have decide that in this case, I will manually mount my shared folder via ssh/nfs in the cases when I need it. 

However I would still be keen to automate a SSH Tunnel as there are some services I want access to. Would this still be a bad idea to put this in the boot process? Or should I just create a script that runs on login?

Also I was wondering if you did no away that I could create the ssh tunnel in a script? The problem being that after I run:
```
ssh me@mydomain -L:1213:10.1.1.1:1213
```
The first problem being asked for a password, and the second being giving a ssh terminal?

I fingered that passing the password in the script or command line would not be good idea and that is properly why I can not find an option to do so. However I remember a while ago when I was trying to automatically mount a windows share, In the fstab I could point to a file witch contained the username and password for the windows domain. And then take away read/write rights away apart from root. Could a similar thing be done?

As for the ssh terminal problem I was wondering if there was just away to push it to the background? However when the script exits then maybe so would the tunnel? I'm not too sure about this!

Thanks heaps MrC

---

### Post by Mr. C. on 2007-03-14
Consider what happens if your laptop is lost or worse, stolen.  If you automatically connect via SSH, anyone who boots your laptop will have access to your system.

Don't place your SSH passwords in files that are not securely encrypted.  Root-only readable provides NO protection against someone who finds your laptop.

The point of passwords is to protect your systems.  Launch your script, enter the password, and let it does its business.

The tunnel stays alive as long as the ssh connection is running.  One you put ssh into the background, it exits when the connection is terminated.  There are special options you need to use to put ssh into the background.

To avoid a pseudo terminal being allocated, use -N.  Read up on the ssh command via

```
man ssh
```
Also note the SSH_ASKPASS variable.

MrC

---

### Post by guysmiley25 on 2007-03-14
Good call on the security! Thanks for that! The whole point of SSH Tunneling is for more security.

I see that the -N switch makes it so you do not have the terminal this is awesome. I still can not work out how to send it into the background.

If I go:
```
ssh me@mydomain -L:1213:10.1.1.1:1213 -N &
```
I am not given the chance to put in my password.

In trying to find away to put ssh into the background I discovered the screen program however I want to automate the process completely.

I could find little information on SSH-ASKPASS, I did not really understand the man. From what I've gathered I can be promoted for a password from a GUI dialog. If this is the case, and since I only need the ports to be accessed when the programs I need access is ran. Could I create a script like the following:

```

# Script for programx
GUI Prompt for Password
SSH Tunnel into mydomain
programx
exit

```

Then chance my shortcut for programx to point to this script. by putting it in my ~/.local/share/application. on my local /home.

Also this way the tunnel would only be opened when then program is running as well.

Thanks again MrC.

---

### Post by guysmiley25 on 2007-03-14
While I'm probing your brain, what about this idea:

```

# Run program on mydomain script.
GUI Prompt Password
SSH into mydomain
run programy on mydomain
exit

```

In otherworld a script witch asks for your passwords and that's the only input. From there the script logs in via ssh to mydomain. And then from the mydomain terminal runs programy.

Then maybe programy could be a script that runs programx, after programx is finished programy closed the ssh sessions. then the first script would exit as that is the last line.

Would be very cool if this could be done.

Thanks.

---

### Post by Mr. C. on 2007-03-14
Right, you're getting the idea now.

You need to use the -f option (and don't need &), and this also implies -N as well.  Read both.  It was designed to allow the program to go into the background after your password has been entered.

Here's a little tutorial that might be helpful:  [http://www.g-loaded.eu/2006/11/24/auto-closing-ssh-tunnels/](http://www.g-loaded.eu/2006/11/24/auto-closing-ssh-tunnels/)

You can be prompted for a "passphrase", which is differnt than as password.  The ssh-add program is designed to add authenticated identities to an ssh key agent (it stores key's, so additional passphrases do not require re-entry).  But this request you set ssh-keys.  It is not difficult, but you'll have to get the concepts straight.

The ssh-add program will call ssh-askpass (and its GUI counterpart gnome-ssh-askpass), which brings up a dialog for passphrase entry.

Until you are ready for that, I'd suggest making a simple Launcher app that starts up a terminal windows, runs your ssh command, which prompts for your password, whereby ssh goes into the background and you can exit the shell.

MrC

---

### Post by guysmiley25 on 2007-03-14
An awesome solution, and that guide you pointed out will help me when I get around to VNC also. But for the program I am using it is somewhat the same.

So I'm using this command here:
```
ssh -f -L 1213:10.1.1.1:1213 me@mydomain sleep 10; myprogram
```

And because of the ~/.local/share/applications/myprogram.desktop. When I'm using the local home. It's all automatic.

So when I'm plugged into my network myprogram works becasue it's setup to use 10.1.1.1:1213. and when I'm not it also works because it's setup to use 127.0.0.1:1213. via the different profiles. This is fantastic.

I would still really like to get the GUI Passkey things working now, Just to make it so much nicer as when I'm running myprogram after I put in my password the terminal windows stays open. Using up my desktop :) And when I close the terminal window. It also closes myprogram.

Maybe it will be easier to find a work around for closing the terminal with out closing myprogram, and then like you suggest myprogram would force the ssh tunnel to remain open.

It would be so nice if ssh added a option to prompt for your password via GUI. But oh well.

So for the GUI passkey "thing!" Do I need to install these programs: ssh-add, ssh-askpass, and gnome-ssh-askpass.

Is gnome-ssh-askpass the only option. It should not be a problem more just wondering. I'm running xfce4 and not gnome.

Is this ssh key a different type of authentication? eg Do I need to configure my ssh server differently? If so will I still be able to ssh in normally? Also if so is this different authentication better worse or same?

Thanks MrC your been fantastic.

---

### Post by Mr. C. on 2007-03-14
That's great news.  I'm really please that the info was what you were looking for.

Start yourself down the path towards moving away from password, and going to a pass phrase configuration.  The rest will come after that.

Pass phrases are far superior because:

  a) they can be arbitrarily long and complex
  b) the use a public / private key pair, known to be very secure
  c) they allow the use of ssh-add to add keys to an "agent" that retains your key, so additional logins do not require passwords (as long as the agent is running).  This is what the ask-pass program uses.

There are probably several good tutorials online - I don't happen to have any quick references, so do a google search for perhaps, openssh key generation.  I would highly recommend the O'Reilly SSH book.

Use locate to see what exists on your system - they should exist:

```
locate ssh-add ssh-askpass gnome-ssh-askpass
```

Once you get an RSA key made, you can disable the weaker password authentication mechanism if you want.

MrC

---

### Post by guysmiley25 on 2007-03-14
OK so using this [guide]("http://kimmo.suominen.com/docs/ssh/") I have done the following:

I did this from my server and laptop while using the shared /home dir.

```

guysmiley@server$ ssh-keygen -t rsa
Generating public/private rsa key pair.
  Enter file in which to save the key (/home/guysmiley/.ssh/id_rsa): [RETURN]
  Enter passphrase (empty for no passphrase): my passphrase
  Enter same passphrase again: my passphrase
  Your identification has been saved in /home/guysmiley/.ssh/id_rsa.
  Your public key has been saved in /home/guysmiley/.ssh/id_rsa.pub.
  The key fingerprint is: blah blah blah

guysmiley@server$ cd ~/.ssh
guysmiley@server$ cp id_rsa.pub authorized_keys

```
```

guysmiley@laptop$ ssh-agent
guysmiley@laptop$ ssh-add
  Enter passphrase for /home/guysmiley/.ssh/id_rsa: my passphrase
  Identity added: /home/guysmiley/.ssh/id_rsa (/home/guysmiley/.ssh/id_rsa)

```

Now I do not need any password or passphrase! While this is convenient it is also scary for the reasons you had mentioned before about losing my laptop.

However just wondering if I getting this correct. This "id_rsa" file. Can anyone can see it and have access to it and still not be able to access my ssh server?

And, if I disable password and just use passphrase I have to have this file to log in. If this is true is it a good idea to disable password, enable passphrase, and put the file somewhere where I can access it. eg FTP/HTTP? Or is it better to leave passwords on.

Oh and can I make it ask for a password using GUI? 

Thanks again.

---

### Post by guysmiley25 on 2007-03-14
Sound like I have to set the  SSH_ASKPASS that you mentioned eailer.

I tryed: export SSH_ASKPASS=ssh-askpass

But no luck.

---

### Post by Mr. C. on 2007-03-14
Once you shutdown your session, the agent purges the keys.  No need to worry.  Don't leave you laptop in hibernation / sleep mode, without a password protecting the box.

The id_rsa file is your private key.  Nobody but you should ever see it.  Keep it as mode 600 or 400, owned by you.

You must have the private key to log in : make available to yourself however is convenient and secure.

SSH allows you to configure the server to accept fall back mechanisms (eg. try public key, next try password).  Get the hang of it for a while, and then you can disable passwords altogether.  Since passwords are generally less secure (eg. they are subject to dictionary and brute force attacks), pass phrases using public key cryptography are better.  They *require* the attacker to have your public key, and the script kiddes and cheap hacks won't be bothered; they'll just use dictionary attacks elsewhere.

To have the GUI ask-pass command work, ASK_SSHPASS must be set *and* the program you are launching *must not have a controlling terminal (eg. anything you type at the keyboard can be thought of as having a controlling terminal).  It was designed to work from some progarm like X 11 that that starts up without a controlling terminal.  If there is a controlling terminal, it will be used to ask for the password.  This should explain why your attempts earlier failed.  Controlling terminal.

Having said all that, you use the ssh-add program to do the work for you.

Create a launcher on your desktop (right click desktop, create launcher).  Give it any name you want.  For the command, use the following:

```
sh -c 'ssh-add </dev/null; gnome-terminal'
```

Save, and then launch it.  You should be asked the password (via GUI!) and then a terminal window will open.

Now terminal doesn't care about a password.  But a remove SSH server would.  so if you create a terminal that connected to your remote ssh server, ssh would use the newly added key to authenticate, and the ssh connection would be established.

Got it ? :-)

MrC

---

### Post by guysmiley25 on 2007-03-15
Ok so this is what I tried

I've got my script for my program as follows:
```

# My Program Launcher
ssh-add </dev/null; gnome-terminal
ssh -f -L 1213:127.0.0.1:1213 me@mydomain sleep 10; programx
ssh-add -D

```

A created a desktop shortcut to the script.

This worked as expected however the terminal displayed an error for the line:
ssh-add </dev/null; gnome-terminal

So I changed it to:
ssh-add </dev/null

So it now is:
```

# My Program Launcher
ssh-add </dev/null
ssh -f -L 1213:127.0.0.1:1213 me@mydomain sleep 10; programx
ssh-add -D

```

And this still give the desired effect. So yay I'm done!

However I would like a clearer understanding of the process.

How come I do not have to put in the path to the file. eg ssh-add mykeyfile. Or is it just because it is in the default location?

If I was sshing into my server from another machine what file do I need. The id_rsa or the id_rsa.pub.

I would have thought that it was id_rsa.pub was the public one and that id_rsa was the private one. However when I run ssh-add </dev/null the dialog whether terminal or GUI it automaticly points to id_rsa. This is very confusing.

Also I would have thought that on the server I would only need the id_rsa, and on remote machines need id_rsa.pub. Now I remember something about authorized_keys as well.

This is getting very confusing.

Also I have not done anything about SSH_ASKPASS. or is it still stored somewhere from when I last did it. Maybe there is a default configuration somewhere.

But it works!!! yay.

Thanks heaps for all the help so far MrC. I could not have done it with out your support.

---

### Post by Mr. C. on 2007-03-15
> **guysmiley25 said:**
> 
And this still give the desired effect. So yay I'm done!

Excellent!

> 
How come I do not have to put in the path to the file. eg ssh-add mykeyfile. Or is it just because it is in the default location?
Your keys are stored in ~/.ssh, the default location for a user.  SSH was built to look there.

> If I was sshing into my server from another machine what file do I need. The id_rsa or the id_rsa.pub.

I would have thought that it was id_rsa.pub was the public one and that id_rsa was the private one. However when I run ssh-add </dev/null the dialog whether terminal or GUI it automatically points to id_rsa. This is very confusing.

Correct.  .pub is public, the other private.  *[correction]* The server provides a challenge, your **public** key is used to encrypt that challenge, and the challenge sent back to the **client**. The **client** then takes this authenticator and decrypts it using your ***private*** key. Furthermore, the client hashes the combination of session id and challenge,  and sends the hashed value to the server *[end correction]*. Therefore the server needs the public key, all the clients you use need the private key.

The authorization file on the server is where you install your public key(s).  This allows you to have many private keys on various machines, and add each of their corresponding public keys to authorized file.

> Also I would have thought that on the server I would only need the id_rsa, and on remote machines need id_rsa.pub. Now I remember something about authorized_keys as well.

Other way around.  Private=your current system, Public=server.

The "authorized_keys" file is for SSH1.  Don't use it; in fact, disable SSH1 on your server and restart the sshd server. Use the "authorization" file for SSH2.

> 
Also I have not done anything about SSH_ASKPASS. or is it still stored somewhere from when I last did it. Maybe there is a default configuration somewhere.


It is like set in the GDM environment already.
> 
But it works!!! yay.

Thanks heaps for all the help so far MrC. I could not have done it with out your support.

Your welcome!
Cheers,
MrC

ps. perhaps its time to change the subject of this thread?

---

### Post by guysmiley25 on 2007-03-15
First thing, How do I change the subject of this thread?

Ok so I think I almost understand it.

On my server I need ```
~/.ssh/id_rsa.pub
```

And on my laptop or any remote client```
~/.ssh/id_rsa
```

Is this correct?


Now is this file for SSH1: ```
~/.ssh/authorized_keys
```

And this file for SSH2: ```
~/.ssh/authorized
```

And the authorized_keys/authorized files are just a list of the keys from the id_rsa.pub file?

So do I need then authorized_keys/authorized on the server or the laptop? This is where I'm confushed I think. Because at least I thought that the authorized_keys went on my laptop and was a list of the keys that I need to connected to remote ssh servers. eg Home/Office etc. But the authorized_keys file is just a copy of the id_rsa.pub file. And don't you need the id_rsa file to connect as well. And therefore you need both files to access the ssh server?

Also to disable SSH1 and enable SSH2, do I just rename authorized_keys to authorized and then restart ssh?

Thanks again MrC.

---

### Post by guysmiley25 on 2007-03-15
Ok this is werid!

From my laptop with local /home. I tryed removing and swaping around the files in ~/.ssh, to see what happens.

So I tryed renaming "id_rsa" to thing, and it did not work. I will assume it will work if I changed my script to ssh-add /path/thing. So I did, but before doing so I renamed "thing" to "thingin".

Forgetting that my script pointed to thing and thing did not exist and thingin did. I ran my script via the desktop shortcut. Non controlling terminal. And guess what, I got a GUI prompt for my password, and not pass phrase.

So I removed ssh-add from my script and now just have:
```
ssh -f -L 1213:127.0.0.1:1213 mydomain sleep 10; myprogram
```

And nothing in my ~/.ssh dir apart from known_hosts

It seems that ssh it just smart enough to know to use a GUI prompt when required. Also it must know from the SSH_ASKPASS which GUI prompt to use.

So now I see there is no connection between the GUI part and the key pairing system.

How do I find out what SSH_ASKPASS is set to?

Thanks, Still want to know about those key files too.

---

### Post by Mr. C. on 2007-03-15
1) Change subject: Edit your first post, Advanced button

2) You have ~/.ssh/id_rsa.pub and ~/.ssh/id_rsa correctly understood.

3) Sorry, use: ~/.ssh/authorized_keys .  I'd was thinking of another SSH version (you don't need the authorization file).

4) ~/.ssh/authorized_keys is just a concatenation of the public (eg. id_rsa.pub) keys.  It goes on the server.  You do not need to retain the id_rsa.pub file on the server once you've placed it into authorized_keys (but you might as well just leave it there).  It is not used on your clients - only the private key (id.rsa) is used on the clients.

5) Disable SSH1 in your /etc/ssh/sshd_config file by setting:

   Protocol 2

and while you are there, set:

   PermitRootLogin no
   AllowUsers guysmileys_username
   AllowGroups guysmileys_group

as well.  This prevents root logins over ssh, and allows only the users/groups listed in AllowUsers and AllowGroups.  All in the name of extra security

Time to start reading "man sshd_config" - lots of options there.

MrC

---

### Post by Mr. C. on 2007-03-15
SSH_ASKPASS is defined with a default value when the ssh programs are compiled.

For example: 
```

pathnames.h:#define _PATH_SSH_ASKPASS_DEFAULT   "/usr/X11R6/bin/ssh-askpass"

pathnames.h:#define ASKPASS_PROGRAM         "/usr/lib/ssh/ssh-askpass"
```

One is a GUI ask pass, the other command line.

MrC

---

### Post by guysmiley25 on 2007-03-17
Cool so I need on my server:
```
~/.ssh/authorized_keys
```

And remote clients need:
```
~/.ssh/id_rsa
```

So does that mean it's id_rsa that I can make avaible to myself, and authorized_keys that I should chroot.

Thank so much for all the info MrC

P.S What should I change the title to, SSH, laptop networking, I'm not sure what it comes under!

---

### Post by Mr. C. on 2007-03-17
> **guysmiley25 said:**
> Cool so I need on my server:
```
~/.ssh/authorized_keys
```
Correct.

> **guysmiley25 said:**
> 
And remote clients need:
```
~/.ssh/id_rsa
```
Correct.

> **guysmiley25 said:**
> 
So does that mean it's id_rsa that I can make avaible to myself, and authorized_keys that I should chroot.
Yes, id_rsa is for your eyes only.  It must be 600 or 400 perms.  Never give it or your passphrase to anyone.  These are your double locks.

I don't understand your term chroot in this context.  You mean chmod 600 ?

> **guysmiley25 said:**
> 
Thank so much for all the info MrC

My pleasure - you're welcome.
> **guysmiley25 said:**
> 
P.S What should I change the title to, SSH, laptop networking, I'm not sure what it comes under!
Good question - whatever you think will help the most people!

MrC

---

