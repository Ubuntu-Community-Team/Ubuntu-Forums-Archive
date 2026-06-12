---
title: "Permissions question"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Mortuis on 2007-05-03
I'm trying to set up bitlbee, but when I run the program I get the following message:
> ERROR :Warning: Permission problem: Can't read/write from/to /var/lib/bitlbee/.
My question is, would it be stupid to change the permissions on /var/lib/bitlbee, or should I redirect bitlbee to use a different directory, like ./.bitlbee/ or something to store it's config files?

---

### Post by obbe on 2007-05-03
i don't know this application..however the error happen when you trying to launch the program by the application menu? or by terminal? you should try to launch it as root..

---

### Post by Mortuis on 2007-05-03
I tried to launch it on the terminal, the computer in question is an Ubuntu Server install, no GUI.

I have tried running it as root, and I get the following message:
> ERROR :Warning: BitlBee is running with root privileges. Why?
Which I took to be a sign that I ought to not be running it as root.

---

### Post by taurus on 2007-05-03
Assuming the name of that command is BitlBee, run it as

```
sudo BitlBee
```

---

### Post by Mortuis on 2007-05-03
Sorry, I should have been more specific.  That's how I got the error message asking why I was running as root.  I'm just reluctant because I understand as a rule of thumb you're not generally supposed to run applications as root, and that message seems to reinforce that.

---

### Post by Churnd on 2007-05-03
Try:

```
sudo chmod +x /var/lib/bitlbee/bitlbee
```

(I'm assuming bitlbee is the executable)

However, I don't know if you would have issues running the program once it launches.  If it does, you might need to make the /var/lib/bitlbee writable by you by changing ownership:

```
sudo chown -R user:group /var/lib/bitlbee
```

Where user:group is your own user and group.

---

### Post by Mortuis on 2007-05-03
I guess the confirmation I was looking for was if it was foolish to change the permissions on that folder or not.  I'm not as familiar with security concepts as I'd like to be and wanted to make sure I wasn't violating a best practice or something by doing so.

---

### Post by Churnd on 2007-05-03
All that would be "vulnerable" would be that one directory, and only if someone guesses your user password.  It would be no more vulnerable than your home directory.  It's not really best practice, but I don't know enough about bitlbee to say why it isn't working correctly.  How did you install it?

---

### Post by Mortuis on 2007-05-03
I installed it with apt-get, I try to stick to the package management system whenever possible.

---

### Post by Churnd on 2007-05-03
Maybe read the manual?  Sometimes you have to add yourself to a certain group for programs to run correctly.

Run the following commands and post their output:

```
sudo ls -l /var/lib/ | grep bitlbee
```
```
sudo ls -l /var/lib/bitlbee
```

---

### Post by Mortuis on 2007-05-03
The documentation is very sparce, the best I get from the man page is the option to use an argument to point it to a different directory.  That's an option that's somewhat of a hassle which I'd rather avoid, but not one I'm unwilling to do.  I just would prefer to be able to use the default directory without doing anything stupid. :-)

> john@gabriel:~$ sudo ls -l /var/lib/ | grep bitlbee
Password:
drwx------ 2 bitlbee nogroup 4096 2007-05-02 07:41 bitlbee
john@gabriel:~$ sudo ls -l /var/lib/bitlbee
total 0

---

### Post by Churnd on 2007-05-03
Ok now I can see why you're getting those errors.  There doesn't seem to be anything in the /var/lib/bitlbee directory, but it's locked out to everybody but the bitlbee user.  The group is left null (nogroup) for a reason... not that it matters because the directory has no group permissions set.

You could:

```
sudo su - bitlbee
```

then run the program, and it should work, but the real key to the puzzle would be to figure out why it was set up that way.  I found this with a few minutes of googling:  [http://www.travishartwell.net/blog/tags/im](http://www.travishartwell.net/blog/tags/im)

---

### Post by Mortuis on 2007-05-04
Thanks for all your help, I got really creative with my google searching and came across [http://f0rked.com/public/bitlbee-user-guide.html](http://f0rked.com/public/bitlbee-user-guide.html) which says under configuration:
> You should create a directory where BitlBee can store it's data files. This should be the directory named after the value 'CONFIG' in Makefile.settings. The default is /var/lib/bitlbee, which can be created with the command mkdir -p /var/lib/bitlbee. This directory has to be owned by the user that runs bitlbee. To make 'nobody' owner of this directory, run chown nobody /var/lib/bitlbee. Because things like passwords are saved in this directory, it's probably a good idea to make this directory owner-read-/writable only.
So I guess I'll just change the directory's permissions.

---

