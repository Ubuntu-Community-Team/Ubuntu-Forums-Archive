---
title: "How do I access permission back on a folder that I accidentally sent to NONE?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2007-06-01
I was trying to make sure that I did not accidently delet a folder with some important papers and such in it, so I went to permission=>access=>none, which I think I now realize also ZERO access. I am trying to gain access to it again, but how do I do this? Just trying to swith it back to read and write gives me a "permission denied" error.

Thanks

---

### Post by yabbadabbadont on 2007-06-01
In Gnome, hit Alt-F2.  Run:
```
gksudo nautilus --no-desktop --broswer
```
Now you should be able to change the permissions.

---

### Post by JonDubya on 2007-06-01
Open up a terminal, and do `chmod 755 folder_name` granted that you are in the directory above the folder.

---

### Post by zazen666 on 2007-06-01
Im using Xubuntu if that helps/makes any difference........

---

### Post by rillip on 2007-06-01
The one sure fire way to do it is what JonDubya said, with a slight modification

sudo chmod 755 folder_name

I think you'll have to be the super user to do it, being that it has its permissions set to none. If, after that, you still get an error, try

sudo chown username:username -u folder_name

where username:username is the username you login with.  This sets you back as the owner; I don't think setting the permissions to "none" would do this, but it's one interpretation.  Most likely it just chmod'd it to 000

You ca likely use 644 as well; this is sufficient for me to do everything I want to do with my files.  Unless you have a script or something in there, you probably won't execute it.

---

### Post by JonDubya on 2007-06-01
> **rillip said:**
> The one sure fire way to do it is what JonDubya said, with a slight modification

sudo chmod 755 folder_name

I think you'll have to be the super user to do it, being that it has its permissions set to none. If, after that, you still get an error, try

sudo chown username:username -u folder_name

where username:username is the username you login with.  This sets you back as the owner; I don't think setting the permissions to "none" would do this, but it's one interpretation.  Most likely it just chmod'd it to 000

You ca likely use 644 as well; this is sufficient for me to do everything I want to do with my files.  Unless you have a script or something in there, you probably won't execute it.
I played around with a folder that I created and didn't need to use the sudo (chmod to 000 & back), but like rillip said, use sudo to guarantee it to work.  This mainly depends on if you're the owner or not of the folder to start with.

---

### Post by zazen666 on 2007-06-01
I keep getting an error saying no such file or directory

Do I need to use this command?

sudo chmod 755 /filename 


I mean, do I need to use a "/" before the file name?

Also, the file name has spaces in it, if that matters.

---

### Post by JonDubya on 2007-06-01
Ok, there's 2 things you can do, if you know the full path to the folder you can do this:

sudo chmod 755 /path/to/folder/folder\ name 
(the \ is to allow for the space, use one for each space)

Otherwise you'll have to navigate to the directory that contains the folder:
cd /dir1
cd dir2
cd dir3 
and so on, then just do sudo chmod 755 folder\ name

If you can provide the actual folder name & path to it, we can give you the actual line of code to enter, but try the other options first.

---

### Post by rillip on 2007-06-01
The spaces DO matter.  If you don't enclose the file, i.e. chmod 'file name' or specifically encode the spaces, it won't find the file.  To encode them it'd be file%20name

Using spaces in Linux file names is a Bad Idea (tm) if you like things the easy way

Edit:  Ah, I forgot about \ as the escape charachter, that should work as well.  I *think* my way will still work, but I'd probably go with \, it's easier.  %20 is used in html at least, and I've seen it in Linux file logs before, so I think it'll figure it out.  Moot point anyway :p

---

### Post by zazen666 on 2007-06-01
x

---

### Post by zazen666 on 2007-06-01
I figured out the spaces issues, but now all the files in the folder area also locked. 
do I have do use the same 
sudo chmod 755 

for each individual file?

---

### Post by rillip on 2007-06-01
You shouldn't have to on each file, try doing man chmod, I believe you can just use -r at the end to make it recursive, i.e. hit all the subfiles too

---

### Post by zazen666 on 2007-06-01
Never mind!!! I got it!!!!

You guys rock---thanks a lot!!!

---

### Post by JonDubya on 2007-06-01
Glad we could help.  I know you would do the same for us.

Jon

---

