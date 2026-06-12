---
title: "confusion about paths and permissions"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by ColmOsiris on 2007-06-21
[I am using the Mac Terminal app to get to my Ubuntu server box via ssh.]

In the Linux command line tutorial I'm going through (from <www.linuxcommand.org>), I've just got to the bit about shell scripts.

Yesterday,  when I opened the Terminal, and forgot to ssh into the Ubuntu box, I created a simple 'Hello World' script using pico, and I ran it using './myscript'. It worked fine.

Today, realising I had not done it on the Ubuntu box, I sshed into it, and did the same thing again. This time I got a 'Permission denied' message.

The permissions for the working directory  ('/Users/username' on the Mac, and '/home/username' on the Ubuntu box) were the same in both cases- 'drwxr-xr-x'.

But the permissions for the script I'd created ('myscript') were different - '-rwxr-xr-x' on the Mac, and '-rw-r--r--' on the Ubuntu box.

Please can someone tell me why the permissions for the script are different, when the permissions for the working directory are the same. And what can I do about it?

Thanks a million. :)

---

### Post by finer recliner on 2007-06-21
macs also have bash installed which is why you can the same script on both OSes.


for the issues with permissions, you need to give your shell script execute permissions (thats what the x stands for in the drwxrwxrwx line. ubuntu requires you to give execute permissions to any files you create. this is a security feature (specifically so that viruses cannot download and run themselves automatically etc)

to give your file execute permissions, cd to the directory the file is contained and then:
```
$sudo chmod u+x myscript
```

more help about how to interpret and change permissions:
[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)
[http://www.zzee.com/solutions/chmod-help.shtml](http://www.zzee.com/solutions/chmod-help.shtml)

---

### Post by ColmOsiris on 2007-06-22
Yes, I know Macs have bash. This is what I am using.

And I wasn't running the same script - one was on the Mac, and one was on the Ubuntu box.

You say "ubuntu requires you to give execute permissions to any files you create" - is this unique to Ubuntu, then? Is this why it was not mentioned in the tutorial? And is this why it is not an issue when running the same thing on the Mac?

---

### Post by st0nes on 2007-06-22
Permissions assigned to files are not dependent on the permissions of the directory in which they reside.  Permissions assigned to new files that you create depend on the "umask" setting in (I think) your .bashrc or .profile file (I know on AIX it is .profile).  When you create a file that needs to be executable, you must explicitly change the file permissions to allow execution (chmod 775 or similar).

---

### Post by ColmOsiris on 2007-06-22
Thanks to finer recliner and st0nes.

I had a look at the '.bash_profile' and '.bashrc' files. I don't understand them, but I don't think I need to at this stage. Well, I hope not, anyway!

So can I assume Linux does not give execute privileges to new files, but other flavours of Linux do?

---

### Post by ColmOsiris on 2007-06-22
> **ColmOsiris said:**
> So can I assume Linux does not give execute privileges to new files, but other flavours of Linux do?

I meant "So can I assume Ubuntu does not give execute privileges to new files, but other flavours of Linux do?"!

Oops!

---

### Post by 3rdalbum on 2007-06-22
As far as I know, other flavours of Linux do the same as Ubuntu in this regard. The execute permission is a simple yet effective security feature, and I'm genuinely surprised that Mac OS X seems to run roughshod over it.

---

### Post by ColmOsiris on 2007-06-23
Yes, it seems to. But surely, if someone creates a script, they would want to run it, wouldn't they, at least to test it? So they'd neet to set at least the owner execute bit.

---

### Post by Inxsible on 2007-06-23
> **ColmOsiris said:**
> Yes, it seems to. But surely, if someone creates a script, they would want to run it, wouldn't they, at least to test it? So they'd neet to set at least the owner execute bit.

Right ! But in the same vein, if a virus comes in an email that you click open, you have just created a file in your harddrive somewhere so you would automatically have execute permissions, and the virus would go about doing its merry business !!

Not something you'd want I believe  !!

---

