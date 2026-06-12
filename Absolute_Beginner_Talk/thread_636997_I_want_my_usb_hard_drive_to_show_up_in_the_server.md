---
title: "I want my usb hard drive to show up in the server"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Kuroda_Shun on 2007-12-10
I have put pictures on an external drive (usb). How am I able to put them in my apache2 server?

---

### Post by Kuroda_Shun on 2007-12-10
Ummm, normally when I post a question I'll get somebody who knows the answer.... anybody? anyone? Buler?

---

### Post by annda on 2007-12-10
you can make a symbolic link to a folder on the disk in the server's document directory. just set the permissions to make sure that directories above are not accessible to the outside world.

---

### Post by Kuroda_Shun on 2007-12-10
I looked up what symbolic link was and I got this, the problem is I have no idea what it means..  whats the~key mean? and the one two three?
" I am so confused"

To create a symbolic link in Unix, at the shell prompt, enter the following command:

ln -s target_filename symlink_filename

Replace target_filename with the relative or absolute path which the symlink will point to. Usually the target will exist, although you can create a symlink to a target which does not exist. Replace symlink_filename with the desired name of the symbolic link. The ln command then creates the symbolic link. After you've made the symbolic link, you can then treat symlink_filename as an alias for the target file. You can use normal file management commands (e.g., cp, rm) on the symbolic link. Commands which read or write the file contents will access the contents of the target file.

user@userbox:~/one$ cd two
user@userbox:~/one/two$ ls
a b
user@userbox:~/one/two$ cd
user@userbox:~$ ln -s ~/one/two three
user@userbox:~$ cd three
user@userbox:~/three$ ls
a b
user@userbox:~/three$ cd
user@userbox:~$ cat ./one/two/a
a
user@userbox:~$ echo "c" > ./one/two/a
user@userbox:~$ cat ./three/a
c

---

### Post by annda on 2007-12-10
hi!

one, two, three are just examples, so don't worry about that. the tilda ~ is a shortcut for your user directory in /home.

basically, you can create a symlink in /var/www like that

[COLOR="Red"]SORRY for confusion, i corrected the order now[/COLOR]
```

sudo ln -s /media/**mydisk/pictures** /var/www/mypictures
```

replace the bold part by the actual disk/directory where you have the pictures. you need sudo to issue this command as root because normal users have no writing access to the server dir.

test it to see if you can access the contents of the dir via browser. if not, the permissions will have to be changed.

---

### Post by annda on 2007-12-10
i forgot: if the external drive is formatted as something else than ext3 and automatically mounted, it will be at least difficult to adjust the permissions...

---

### Post by Kuroda_Shun on 2007-12-10
Thank you. I will give it a try when I get home. yes I think the permissions will be difficult to set because it is auto mounted. By any chance can I um mount it then try it?
But anyway thank you for responding....

---

