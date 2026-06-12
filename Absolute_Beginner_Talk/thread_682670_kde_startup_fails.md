---
title: "kde startup fails"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Mr.Carramba on 2008-01-30
hi!

I'm not shore what I have done with user account but know when I enter password at login screen I only get black splash and when return to login screen. the user in question have admin right and was created during install
how should I restore it?

would it work to remove user accout from other admin and recreate?

---

### Post by doddo on 2008-02-02
Hello! If recreating user account will work or not depends on y ur screen is black

Have you selected a proper window manager/desktop environment from gdm menu??


I think u should try to create a testuser and log in with that user to see if the problem is with ur current user or not

hit CTRL+ALT+F1
and log in using ur name

Then do 
sudo adduser testuser



then hit CTRL+ALT+F7 and log in with that user and see if u still get problems with login.

---

### Post by Mr.Carramba on 2008-02-02
> **doddo said:**
> Hello! If recreating user account will work or not depends on y ur screen is black

Have you selected a proper window manager/desktop environment from gdm menu??


I think u should try to create a testuser and log in with that user to see if the problem is with ur current user or not

hit CTRL+ALT+F1
and log in using ur name

Then do 
sudo adduser testuser



then hit CTRL+ALT+F7 and log in with that user and see if u still get problems with login.

well I have several other users on computer and non of them have problem to logging in. I think I have have added/removed some wrong group that user belongs to. just have to figure out which one is that

---

### Post by doddo on 2008-02-02
In that case, I think that it is more likely that something is messed up in ur ~/.kde folder

if u do something like this

```
mv /home/ur_user/.kde /home/ur_user/.kde_old
```

And then log into ur account with your user.

This should prompt kde to create another .kde folder with settings in it for your user.

.kde stores all settings for ur user in that folder (it might use other folders aswell, but that folder is perfect to start with)

---

### Post by Mr.Carramba on 2008-02-03
> **doddo said:**
> In that case, I think that it is more likely that something is messed up in ur ~/.kde folder

if u do something like this

```
mv /home/ur_user/.kde /home/ur_user/.kde_old
```And then log into ur account with your user.

This should prompt kde to create another .kde folder with settings in it for your user.

.kde stores all settings for ur user in that folder (it might use other folders aswell, but that folder is perfect to start with)


well I did that but unfortunately I have the same problem, then trying to log in I get black screen and get kickt back to log in screen ...

---

### Post by doddo on 2008-02-03
strange! OK change approach

this can either be a permission issue in which case a

```
 sudo chown -R uruser:urgroup /home/uruser
```

should solve it

if you dont care bout ur settings and this too fails, then i suggest that you make something like this

```
sudo  mv /home/uruser /home/uruser_OLD
sudo cp -a /etc/skel /home/uruser
sudo chown -R uruser:urgroup /home/uruser
```

And see if that helps. If it does you can copy your files and configuration to your new home...

Also, it would be interresting to know what messeges are sent to the TTY spawning the process. If the previous trials tail may I suggest you do a

```
sudo /etc/init.d/gdm stop
echo "exec kde" >> /home/uruser/.xinitrc
startx
```

Then any error messeges should be logged in the TTY from which u ran the program

for instance if u started from tty1 (CTRL+ALT+F1) then any useful error messages would be there.

---

