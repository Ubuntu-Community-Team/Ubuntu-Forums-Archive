---
title: "Absolute beginners - How do I get Bluefish perm to write in /var/www/htdocs"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by LadyLuck on 2006-12-26
Hi yet again. 

I am writing some simple text files for html and php to store in /var/www/htdocs where I view them with Firefox. How do I give Bluefish the privil. to write to that directory. So far I have used a standard text editor e.g.

sudo pico filename.html

but as thing grow and get complicated I would like to use some helpful tool like Bluefish. I have changed filepermissions to rwxrw in the directory to no avail. I know I can write to a directory under my user-id and then use "sudo cp" but this is not what I am looking for. Appreciate any guidance.

Cheers
LL

---

### Post by po0f on 2006-12-26
LadyLuck,

You can add yourself to the group that owns /var/www.  To figure that out, do:
```
[FONT="Courier New"]$ ls -l /var | grep www[/FONT]
```
I don't know about Apache, but LightTPD uses the www-data group, so to add yourself to that group, do a:
```
[FONT="Courier New"]$ sudo gpasswd -a <user_name> www-data[/FONT]
```
Log out and log back in for it to take effect.  You should now be able to write to that directory.  Oh yeah, make sure the group has write permission as well:
```
[FONT="Courier New"]$ sudo chmod g+w -R /var/www[/FONT]
```
That will recursively add write permission to /var/www and all the files and directories underneath it.

---

