---
title: "Permission problem"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-09-26
Hello,

If I run this program (also as root):
```
<?php
$fileName="test2.txt";
print "Writing to $fileName<br>";
$fp=fopen($fileName, "w") or die("Couldn't open $fileName");
fwrite($fp, "Hello world\n");
fclose($fp);
print "Appending to $fileName<br>";
$fp=fopen($fielName, "a") or die("Couldn't open $fileName");
fputs($fp, "And another things\n");
fclose($fp);
?>
```

I get this error message:
> Writing to test2.txt

Warning: fopen(test2.txt) [function.fopen]: failed to open stream: Permission denied in /var/www/listing11.13.php on line 10
Couldn't open test2.txt

I don't know how I can slove this problem. Could you help me, please?

Thanks,
L-B

---

### Post by buckethead27 on 2006-09-26
I see that it does it also as root. - Have you used the command su or did you use sudo? If you haven't tried su, type in sudo su, and then your password, and try again. If not, then as root type in chmod 777 /test2.txt

---

### Post by Cruz on 2006-09-26
Does test2.txt already exist? 
Yes: what are the permission flags on it? Maybe not even root can write it.
No: what are the permission flags on the directory you are working in?

---

### Post by buckethead27 on 2006-09-26
> **Cruz said:**
> 
No: what are the permission flags on the directory you are working in?


Ooo yes! If it is a root directory then use```
sudo nautilus
```

---

### Post by linux-beginner on 2006-09-26
I loged in as root and then I ran the program.
I'm realy newbie and don't know much about using su and sudo. Could you tell me what I can do from a normal user (not root) to run the program without error?

---

### Post by buckethead27 on 2006-09-26
> **linux-beginner said:**
> I loged in as root and then I ran the program.
I'm realy newbie and don't know much about using su and sudo. Could you tell me what I can do from a normal user (not root) to run the program without error?

You can usually run all programs from a normal user, but must sudo or su to install it from the console.

---

### Post by linux-beginner on 2006-09-26
Yes. That is a root directory but I don't know how I can use ```
sudo nautilus
```!

---

### Post by buckethead27 on 2006-09-26
> **linux-beginner said:**
> Yes. That is a root directory but I don't know how I can use ```
sudo nautilus
```!

Jump in to a console and type it in
Applications>Accessories>Terminal(Console)


Edit for add: It will open up a file explorer, but with root privaliges.

---

### Post by linux-beginner on 2006-09-26
Do you mean that I must type in the consule > sudo /var/www/listing11.13.php
If I type the above code in consule then get this error:
> sudo: /var/www/listing11.13.php: command not found

---

### Post by buckethead27 on 2006-09-26
> **linux-beginner said:**
> Do you mean that I must type in the consule 
If I type the above code in consule then get this error:

Are you trying to edit the file? If so type in ```
sudo gedit /YOURDIRECTORY/YOURFILE.FILEEXT
```

---

### Post by Cruz on 2006-09-26
He just wants to run a simple PHP Script, there is no reason why he should do it as root, but there are millions of reasons against it.

Dude, can you find the Applications -> Accessoirs -> Terminal thing? Open it and type:

touch test2.txt
chmod 644 test2.txt

This creates the test2.txt file in your home with the right permissions.
Make sure your PHP script is in your home directory and execute it there as your normal user.

---

### Post by buckethead27 on 2006-09-26
> **Cruz said:**
> He just wants to run a simple PHP Script, there is no reason why he should do it as root, but there are millions of reasons against it.

Dude, can you find the Applications -> Accessoirs -> Terminal thing? Open it and type:

touch test2.txt
chmod 644 test2.txt

This creates the test2.txt file in your home with the right permissions.
Make sure your PHP script is in your home directory and execute it there as your normal user.

I appologize for the misunderstanding. I didn't recognize it as a script.

---

### Post by linux-beginner on 2006-09-26
What do you mean of i edited the file?
Why should I edit the file?

---

### Post by buckethead27 on 2006-09-26
> **linux-beginner said:**
> What do you mean of i edited the file?
Why should I edit the file?

It was a giant misunderstanding on my part. I didn't recognize it as a PHP script. ](*,)

---

### Post by enopepsoo on 2006-09-26
But if he is running from /var/www he is wanting to host it on his default site with apache.  I think he should set the permissions on that folder so that his php parser has r/w access there.

I am not really an expert on this stuff (when I set up something similar I used a site in my home folder).  It may be best to wait for an apache genius to come along.](*,)

---

### Post by buckethead27 on 2006-09-26
> **enopepsoo said:**
> But if he is running from /var/www he is wanting to host it on his default site with apache.  I think he should set the permissions on that folder so that his php parser has r/w access there.

I am not really an expert on this stuff (when I set up something similar I used a site in my home folder).  It may be best to wait for an apache genius to come along.](*,)

I'm sure there is a tutorial. Search the fourms or google it.

---

### Post by Cruz on 2006-09-26
> **linux-beginner said:**
> Do you mean that I must type in the consule 
If I type the above code in consule then get this error:

Type "sudo php /var/www/listing11.13.php" then.
Is this script for command line use or is it actually going to be served by apache?

---

### Post by linux-beginner on 2006-09-26
Let me ask how I can set permission r/w on the folder "/var/www"

---

### Post by buckethead27 on 2006-09-26
> **linux-beginner said:**
> Let me ask how I can set permission r/w on the folder "/var/www"

If i'm not mistaken (which i very well might be), type in ```
chmod 777 /var/www
```

---

### Post by xyz on 2006-09-26
This may help a newcomer (Hey Welcome!) as overall introduction to understanding bit what's going on:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

It may be a good idea to begin from the start and not jump toooo fast to what can look like absolute medieval chinese dialect. one step at a time so you don't get discouraged. Hang in there!
Let us know...

---

### Post by buckethead27 on 2006-09-26
> **xyz said:**
> This may help a newcomer (Hey Welcome!) as overall introduction to understanding bit what's going on:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

It may be a good idea to begin from the start and not jump toooo fast to what can look like absolute medieval chinese dialect. one step at a time so you don't get discouraged. Hang in there!
Let us know...

I might have to read up on that as well! Thanks!

---

### Post by xyz on 2006-09-26
> I might have to read up on that as well! Thanks!
It sure helped me and ...to tell the truth, it still does but don't tell anybody!! ;)

---

### Post by linux-beginner on 2006-09-26
Thanks a lot for all information!

---

