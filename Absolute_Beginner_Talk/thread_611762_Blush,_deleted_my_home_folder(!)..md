---
title: "*Blush*, deleted my home folder(!)."
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-11-13
Feel like an idiot, naiv idiot... I asked for help regarding compiz([http://ubuntuforums.org/showthread.php?p=3763013&posted=1#post3763013](http://ubuntuforums.org/showthread.php?p=3763013&posted=1#post3763013)), and got an answer to paste a command into the terminal and post the answer. I know, stupid of me &#8211; but I am so used to this from answers that I have got before. The good news; I have not transferred my personal stuff from Windows jet, and I always have a secure backup on an external harddrive. 

But this command deleted all my folders, and I need help to get them back as before(I am talking about empty folders now). I want to have the &#8220;Document&#8221; folder, the &#8220;Ebook&#8221; folder and so on, but If I make them now they will appear on the desktop(cus the Destkop folders is also deleted), and not in my home folder(but if I got to /home/sam the folders are there, but I dont want them on the desktop. Hope this makes sence...

So; I have the homefolder, but when I make a new folder in this folder with nautilus it appears on the desktop, witch I dont want. I want the default Ubuntu solution. 

Damn, stupid me.... Anyone that could tell me how to fix this. Well, lesson learned, next time I will wait for a while to see if others gives a warning before I run anything, perhaps use google to check what the command will do.

Edit: looks like am not the only one; [http://ubuntuforums.org/showthread.php?t=611720](http://ubuntuforums.org/showthread.php?t=611720)

---

### Post by Tux.Ice on 2007-11-13
No idea try backing up most of your data and reloading gutsy or feisty or whatever yur using you could also try creating a new user 

tux

---

### Post by carlosjuero on 2007-11-13
> **_sAm_ said:**
> Feel like an idiot, naiv idiot... I asked for help regarding compiz([http://ubuntuforums.org/showthread.php?p=3763013&posted=1#post3763013](http://ubuntuforums.org/showthread.php?p=3763013&posted=1#post3763013)), and got an answer to paste a command into the terminal and post the answer. I know, stupid of me &#8211; but I am so used to this from answers that I have got before. The good news; I have not transferred my personal stuff from Windows jet, and I always have a secure backup on an external harddrive. 

But this command deleted all my folders, and I need help to get them back as before(I am talking about empty folders now). I want to have the &#8220;Document&#8221; folder, the &#8220;Ebook&#8221; folder and so on, but If I make them now they will appear on the desktop(cus the Destkop folders is also deleted), and not in my home folder(but if I got to /home/sam the folders are there, but I dont want them on the desktop. Hope this makes sence...

So; I have the homefolder, but when I make a new folder in this folder with nautilus it appears on the desktop, witch I dont want. I want the default Ubuntu solution. 

Damn, stupid me.... Anyone that could tell me how to fix this. Well, lesson learned, next time I will wait for a while to see if others gives a warning before I run anything, perhaps use google to check what the command will do.

Edit: looks like am not the only one; [http://ubuntuforums.org/showthread.php?t=611720](http://ubuntuforums.org/showthread.php?t=611720)
The way to do it would be to log into the GUI under that user and allow GNOME (or KDE) to rebuild the Desktop folder. Then get into the Shell and create the other folder structure that you need.

Folders created outside of the Desktop folder should not appear automatically on the desktop (heck, you should be able to create a Desktop folder from the terminal and have it recognized as such).

So try logging in that user to GNOME (or your preferred X Client), make sure everything loads right - then load the Terminal and start creating the folder structure (or just open up the home folder in Nautilus).

For future safety, you can always back up the entire structure of your Home folder by either Zipping(/raring/GZing) the whole thing up and storing it somewhere safe, or by using Home Folder Backup (It is in the repositories).

Edit: Just read about what you probably did - the -rf switch could cause issues. Did you remove the entire /home folder structure? or just the home folder for the current user?

---

### Post by Inxsible on 2007-11-13
Was the user name peodlelol?

He/She is a miscreant. He did the same in another thread and the OP lost all his settings in the home folder too.

If you did a <obscured - pricechild> , then you lost everything on your home drive. all your settings and apps.

You can : 
1) install all the apps again -- which is still not a guarantee that everything will work, since you may miss a few 
2) Re-install Ubuntu.

I normally keep a backup of my home folder using [rsync]("http://www.psychocats.net/ubuntu/backup").

---

### Post by _sAm_ on 2007-11-13
Yes, that was the name, and the command. Lesson is learned, so I will be more carefully in the future before I run what people suggest. Hard learning I guess. 

Thanks for the answers - I will indeed learn how to use rsync before I transferee my personal files from windows, thanks for the tip.

---

### Post by bulldog on 2007-11-13
> **_sAm_ said:**
> Yes, that was the name, and the command. Lesson is learned, so I will be more carefully in the future before I run what people suggest. Hard learning I guess. 

Thanks for the answers - I will indeed learn how to use rsync before I transferee my personal files from windows, thanks for the tip.

Next time,quote the command and report to the forum admin.

---

### Post by philinux on 2007-11-13
Is this idiot sending private messages to people?

---

### Post by someoneouthere on 2007-11-13
this command exept from deleting the home folder does affect other regions like admin rights?

---

### Post by Inxsible on 2007-11-13
> **philinux said:**
> Is this idiot sending private messages to people?No he posted in the thread. I reported one instance and then his posts were taken off the thread. However, the OPs executed the commands before the posts were removed :(

---

### Post by Inxsible on 2007-11-13
> **someoneouthere said:**
> this command exept from deleting the home folder does affect other regions like admin rights?
No. It simply removes everything from your home folder.

---

### Post by hyper_ch on 2007-11-13
> **_sAm_ said:**
> Yes, that was the name, and the command. Lesson is learned, so I will be more carefully in the future before I run what people suggest. Hard learning I guess. 

Thanks for the answers - I will indeed learn how to use rsync before I transferee my personal files from windows, thanks for the tip.

well, you can also go for post count ;) a person with a lot of posts here is not likely to give out nasty commands... someone with a low count (let's say below 100 posts) might mean good by the advice but in that case think first and check what a command is doing before issuing it.

---

### Post by Tyke91 on 2007-11-13
just a tip, the command "rm" removes a folder, so if anyone gives you anything with "rm" in it, and you don't want to remove things, don't listen to them.

---

### Post by taurus on 2007-11-13
> **Tyke91 said:**
> just a tip, the command "rm" removes a folder, so if anyone gives you anything with "rm" in it, and you don't want to remove things, don't listen to them.

Actually, that's not true.  it's just a basic remove command.  If you want to remove an empty directory (NOT folder), you would use rmdir.

---

### Post by _sAm_ on 2007-11-13
> **hyper_ch said:**
> well, you can also go for post count ;) a person with a lot of posts here is not likely to give out nasty commands... someone with a low count (let's say below 100 posts) might mean good by the advice but in that case think first and check what a command is doing before issuing it.

I understand the logic of this, but on the other hand I have seen lots of post by new useres that clearly shows that they are very good with Linux - and have used it a lot. Lets say a old Red Hat user gives the solution for my problem, in his first post - then I would listen. 

This could end up as a problem for forums like this, regarding Linux. Not for me, I have learned my lesson(indeed he he).
You see, not all know much about Linux when they decide to try it out. They get problems, small or bigger, and perhaps they are searching around for some time to find out a solution. When they don&#8217;t find it, they might be sick of it, and will not think twice when a friendly person is offering a solution. And why shouldn&#8217;t they, they have perhaps got help many times before without any trouble. That was my situation; I just wanted to fix my problem as fast as possible so I just did as always; pasted the command and pressed enter. I know this was stupid, I mean, there is commands that will delete entire Linux(!). But I was just not thinking at all. And I didn&#8217;t think of idiots like thisl; all on this forum has been so nice up until now. 

Is there a solution for this kind of abuse, I can&#8217;t think of one myself, but this can really damage a forum and/or a distro imho. 

Are we facing a new type of &#8220;virus&#8221; here.

---

### Post by hyper_ch on 2007-11-13
well, just don't trust blindly anything... linux actually wants you to think... use your brain ;)

and on that principle it's more safely to assume that someone with quite a few number of posts possibly doesn't mean malice... however also someone with no post can give you the solution... but just be careful ;)

---

### Post by steve.horsley on 2007-11-13
What I suggest is this:
Create a second user (System->Admin->Users&Groups). 
Make this second user a member of the Admin group.
Log out, and in as the second user.
Have a look in this new users folder, and copy all his directories to yours.

---

### Post by Tyke91 on 2007-11-14
> **taurus said:**
> Actually, that's not true.  it's just a basic remove command.  If you want to remove an empty directory (NOT folder), you would use rmdir.

I stand corrected, and I've learned something new about linux. Hurray :D

---

### Post by sports fan Matt on 2007-11-14
 if im thinking logically, the home folder is link the I386 folder in M$ so everything would get deleted like what the OP said this making the computer not boot, yes/no?

---

### Post by hyper_ch on 2007-11-15
no, /home folder is like "document & settings" on windows. Computer should still be bootable.

---

### Post by Paulmd on 2007-11-15
> **_sAm_ said:**
> Feel like an idiot, naiv idiot... I asked for help regarding compiz([http://ubuntuforums.org/showthread.php?p=3763013&posted=1#post3763013](http://ubuntuforums.org/showthread.php?p=3763013&posted=1#post3763013)), and got an answer to paste a command into the terminal and post the answer. I know, stupid of me &#8211; but I am so used to this from answers that I have got before. The good news; I have not transferred my personal stuff from Windows jet, and I always have a secure backup on an external harddrive. 

But this command deleted all my folders, and I need help to get them back as before(I am talking about empty folders now). I want to have the &#8220;Document&#8221; folder, the &#8220;Ebook&#8221; folder and so on, but If I make them now they will appear on the desktop(cus the Destkop folders is also deleted), and not in my home folder(but if I got to /home/sam the folders are there, but I dont want them on the desktop. Hope this makes sence...

So; I have the homefolder, but when I make a new folder in this folder with nautilus it appears on the desktop, witch I dont want. I want the default Ubuntu solution. 

Damn, stupid me.... Anyone that could tell me how to fix this. Well, lesson learned, next time I will wait for a while to see if others gives a warning before I run anything, perhaps use google to check what the command will do.

Edit: looks like am not the only one; [http://ubuntuforums.org/showthread.php?t=611720](http://ubuntuforums.org/showthread.php?t=611720)


Look Here:

[http://recover.sourceforge.net/unix/](http://recover.sourceforge.net/unix/)

Unfortuantely the answer isn't that good for non-text documents.

---

### Post by hyper_ch on 2007-11-15
_Sam_ It's also wise to make backups in a regular interval. With the power of rsync and hardlinks I make backups every 6h and back for 90 days ;)

---

