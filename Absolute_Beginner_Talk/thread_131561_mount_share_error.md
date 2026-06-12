---
title: "mount share error"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by dannemil on 2006-02-16
I am trying to mount a remote windows share on my ubuntu machine, and it mounts, but I get this error that appears to indicate that it did not mount.

22389: session request to 128.xx.xx.xx failed (Called name not present)

(I replaced the actual server IP with xx above)

Here is the command to mount the share from a terminal:

smbmount //128.xx.xx.xx/home ~/mnt/localmachine/home/ -o username=somebody,password=yyyyyyy

(The above is all one line)

So when I look after this comment is issued on my local machine, the remote directory has been mounted, but the error message noted above always follows the command.

Is there something wrong with the command that produces this error message (or maybe it's just a warning because it does mount)?

---

### Post by Robgould on 2006-02-16
remove the smbmount - needs a little rearrangeing.

like this
```

//128.xx.xx.xx/home   /mnt/localmachine/home   smbfs    rw,username=sombody,password=yyyyy,uid=1000,gid=1000   0 0

``` 
I think you will like it better.

---

### Post by dannemil on 2006-02-16
[QUOTE=Robgould]remove the smbmount - needs a little rearrangeing.

like this
```

//128.xx.xx.xx/home   /mnt/localmachine/home   smbfs    rw,username=sombody,password=yyyyy,uid=1000,gid=1000   0 0

``` 
I think you will like it better.[/QUOTE]

Thanks, but I tried typing that in with the correct information from a terminal and got the following:

bash: //128.xx.xx.xx/home: No such file or directory.

---

### Post by Robgould on 2006-02-17
I'm sorry.  I read your original post wrong.  You were mounting from the terminal. 
 
What I put is the entry you would make in your fstab file.
 
If you add that line to the end of your /etc/fstab file, the share will be mounted automatically for you when you log on.
 
to do this
```

sudo gedit /etc/fstab

```
This will open the file in gedit.  Add the line to the end of your file and hit enter to move the insertion point to the begining of the next line.
 
Save and close the file.
```

sudo mount -a

```
If everything went right you will get no error.  Browse in nautilus to your newly mounted drive.

---

### Post by Robgould on 2006-02-17
This is a link to a post I made on another forum on the same subject.  The first post shows how to mont from terminal.  There is more info there as well.  You would modify the variables of this statement to fit your situation.  if you do it like this you will be prompted for password, or you can try adding it to the command.  I hope all this helps.
 
```

[LEFT]mount -t smbfs -o username=administrator //Cilent IP/c$ /mnt/[/LEFT]

```
[http://forums.fedoraforum.org/showthread.php?t=76608]("http://forums.fedoraforum.org/showthread.php?t=76608")

---

