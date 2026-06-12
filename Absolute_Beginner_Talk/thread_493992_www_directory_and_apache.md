---
title: "www directory and apache"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by davek17 on 2007-07-06
I'm trying to make a website that'll allow me to create directories and upload to them in my www directory, the problem is everytime i create at directory remotely it is locked and i cannot write to it, how can i change the permissions of a subdirectory of my www directory so that everything written to it is not locked and is accessable by everyone?

Thanks

---

### Post by Rocket2DMn on 2007-07-06
you can chmod to change permissions or chown to change owner.  A -R performs the operation recursively on directories.
```
sudo chmod 755 -R username /var/www/ (or other apache directory)
and/or
sudo chown -R username /var/www/
```

---

### Post by twiceasworn on 2007-07-06
Edit:  Nevermind :)

---

### Post by davek17 on 2007-07-06
But what i mean is, everytime i create a new directory in my www directory via a website from a different computer i have to go back to my server to unlock the directory before i can actually put anything in it.

---

### Post by Rocket2DMn on 2007-07-06
What website aer you using to do this?  
If that website is accessing your machine with root privileges, the directory will be created as so, and you may not be able to access it when logged in with your username.

---

### Post by davek17 on 2007-07-06
I have just been using simple php on a website i create myself, the website is hosted on my ubuntu machine and i've been accessing it through my windows machine and firefox, i just checked the directory i created and it says the owner is www-data, i was thinking maybe everything i do through via the internet would use that name but if so you'd think it'd let me add stuff to that directory using the same system that created the directory but it wont.  Do i have to set everthing that created by www-data to be accessible and modifyable by everyone somewhere in my ubuntu settings maybe?

---

### Post by Rocket2DMn on 2007-07-06
No, basically all that should need to match up is the username that apache is running under and ower/permissions on that apache directory and subdirectories.
the 755 for chmod gives the owner full read/write/execute access and the 5's let anybody else read and execute (ie internet uers).
If you gave the php script access to the machine with username www-data, that is the username it should create directories using.  Maybe you could just add into the script the chmod command so you don't have to login every time to change the permissions.
And no, you don't want anybody to be able to modify, just access.

My preference would be to just use FTP to transfer files and directories, but if the script is what you want, it should be OK.

Do me a favor, create a directory using your script then login to the machine and tell me who the owner of the folder is using 
ls -l

---

### Post by twiceasworn on 2007-07-06
I would suggest the same thing.  You can add into the php script to have it chmod after creation.  Or alternatively you could write a perl or shell script to do the same thing and have it run as a cron job or something.  There are a lot of ways around it.  Could you post the php code you have?

---

### Post by davek17 on 2007-07-06
I think i get you.  I need to change is so that php uses the name 'dave' as thats what i'm logged into as on my server rather than using the name www-data.

---

### Post by Rocket2DMn on 2007-07-06
> **davek17 said:**
> I think i get you.  I need to change is so that php uses the name 'dave' as thats what i'm logged into as on my server rather than using the name www-data.

Yup, should only be necessary if Apache is running under "dave" though, since root can read/write everything.  If it's only your personal access that's a problem, it sounds like the ownership issue.  If you change it so the script login is "dave", but it still doesn't work, add the permissions portion with "chmod 755" so people can access everything from the internet.

---

### Post by davek17 on 2007-07-06
Yeah i have apache logged in as dave as its easier to have it running under dave than root, the php i was using is:

function createDir($dirName){
    if(!is_dir($dirName)){
        mkdir($dirName, 0755);
    }

how do i change my script login, i assume thats somewhere in a php settings file on my server somewhere.

---

### Post by Rocket2DMn on 2007-07-06
That php script probably needs to have dave as the owner.
Check the permissions with ls -l, if the owner is something other than dave, run
```
chown dave scriptname.php
```

---

### Post by az on 2007-07-06
> **davek17 said:**
> But what i mean is, everytime i create a new directory in my www directory via a website from a different computer i have to go back to my server to unlock the directory before i can actually put anything in it.

Automating the process (or simply making that directory world-writeable) is a little dangerous.  The last think you want is for some cracker to upload code to your box, especially if it can get executed by php.

Thje less the webserver can write to your filesystem, the better.

---

### Post by davek17 on 2007-07-06
Thanks i've sussed it, and dont worry about the security issues, it'll all be heavilly guarded and php will be secured to only allow it to execute what i want it to etc, and it wont have root access so its all good.

---

### Post by az on 2007-07-06
> **davek17 said:**
> Thanks i've sussed it, and dont worry about the security issues, it'll all be heavilly guarded and php will be secured to only allow it to execute what i want it to etc, and it wont have root access so its all good.

If anyone could assure that php only executes what they want it to, the network security profession could retire.  And it doesn't have to be root to exploit a vulnerability (and become root or the equivalent).  EDIT:  Ever heard of a web server that ran as root?  How come there are still exploits, then?

Good luck.

---

