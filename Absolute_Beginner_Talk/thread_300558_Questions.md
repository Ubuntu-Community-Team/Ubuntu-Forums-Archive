---
title: "Questions"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-11-15
I'd appreciate the answer to these questions:

1.  What does the tilde (~) represent in a path name?  I read in the system documentation that it represents the user's home directory (/home/username) but in a terminal when I type cd $home, the directory /root is opened with command prompt root@ComputerName:~#

2.  How can I get my Search For Files function to work?  Often when I search on the name of a folder that I'm looking at in a Nautilus window with Look In=folder File System the search comes up empty.

3.  What is the significance of a file or folder name that begins with a dot, as in .Gnome2?  In a terminal when I execute a [I]dir[I] command I have to add the -a option to list the file.

4.  What is the difference between the terminal commands *dir* and *ls*?

5.  Whenever I enter in a terminal the command *gedit* filename, the following is returned:  "(gedit:16015): GnomeUI-WARNING **: While connecting to session manager:Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."  I still get the text editor, functioning normally.  What does this mean?

That's enough for now.  Thanks in advance.

Buck

---

### Post by aidanr on 2006-11-15
i can help with 3 and 4, the . before a file or folder means it's a hidden file. if you look at /bin/ls and /bin/dir they are both the same size, they both have the same man page and --help output and are both written by rms and david mackenzie so i'd say it's pretty safe to say that dir is just a copy of ls for people who are used to dir in windows

dont know about the other 3, they all work as expected for me, i don't have those same problems:-k

---

### Post by PilotJLR on 2006-11-15
> **Buck2348 said:**
> 1.  What does the tilde (~) represent in a path name?  I read in the system documentation that it represents the user's home directory (/home/username) but in a terminal when I type cd $home, the directory /root is opened with command prompt root@ComputerName:~#

Tilde also represents the current user's home directory. For example, if my username is bob, then ~/music would be /home/bob/music.
A faster way to get to your home directory is to just type "cd" and press enter.

> **Buck2348 said:**
> 
2.  How can I get my Search For Files function to work?  Often when I search on the name of a folder that I'm looking at in a Nautilus window with Look In=folder File System the search comes up empty.

No idea why it isn't working for you... it should be, of course. Rather than spend time on that, strongly consider installing the far more powerful program beagle. There is a good wiki article on it... beagle is a lot like google desktop. It can find text quickly from inside pdf's, email, odf files, etc. Very useful.

---

### Post by CatKiller on 2006-11-15
> **Buck2348 said:**
> I'd appreciate the answer to these questions:

1.  What does the tilde (~) represent in a path name?  I read in the system documentation that it represents the user's home directory (/home/username) but in a terminal when I type cd $home, the directory /root is opened with command prompt root@ComputerName:~#

/root is the home directory of root. If you've mischievously logged in as root (either "properly" or with a **sudo -i**) then of course **cd ~** or **cd $home** will take you to /root. That's what they're supposed to do.

> 2.  How can I get my Search For Files function to work?  Often when I search on the name of a folder that I'm looking at in a Nautilus window with Look In=folder File System the search comes up empty.

3.  What is the significance of a file or folder name that begins with a dot, as in .Gnome2?  In a terminal when I execute a [I]dir[I] command I have to add the -a option to list the file.

As aidanr says, files whose names start with a . are hidden. As **man dir** says: >        -a, --all
              do not ignore entries starting with .


> 4.  What is the difference between the terminal commands *dir* and *ls*?

**dir** is an alias for **ls** for those people who keep typing the wrong thing. Possibly *dir='ls --color=auto --format=vertical'*, although I don't know a huge amount about it.

Try them both. You'll see the difference.

> 5.  Whenever I enter in a terminal the command *gedit* filename, the following is returned:  "(gedit:16015): GnomeUI-WARNING **: While connecting to session manager:Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."  I still get the text editor, functioning normally.  What does this mean?

Are you sure it's not when you **gksudo gedit**? (Or **gksudo** anything for that matter, or **gksu**?) In which case it's a message that doesn't really mean anything. It's a low-priority bug.

---

### Post by Buck2348 on 2006-11-16
I begin to think I'm too stupid, or Linux is too smart, for me to use it.  I can't figure out how to quote selectively what I'm answering here so it will have to go without quotes.

I don't know how I could log in as root, mischievously or otherwise--I've been told about a hundred times that in Ubuntu this can't be done.  I installed a script given in System, Help, System Documentation, Ubuntu Desktop Guide, Configuring Your System, Desktop Tricks, sec. 4.1.10 Open files with administrative privileges from the file manager.  I tried removing the script and rebooting, with no result.  dir with no argument or dir ~ always takes me to /root, not /home/user.  I also disabled automatic log-in and manually logged in as myself, with the same result.

I installed Beagle and followed the brief instruction for enabling indexing.  The Search menu makes me wonder what it's supposed to be doing because although "everywhere" is at the top of the list, the rest of the list doesn't mention anything about the file system.  At any rate it has yet to find anything in the way of a folder or file that I've entered.

Thanks all for your replies.

---

### Post by CatKiller on 2006-11-16
> **Buck2348 said:**
> I begin to think I'm too stupid, or Linux is too smart, for me to use it.  I can't figure out how to quote selectively what I'm answering here so it will have to go without quotes.

Sorry if it was me that made you feel that way. I certainly didn't intend to.

The icon that looks like a "forward", the envelope with the arrow, allows you to "tag" messages to be quoted. The other one, that looks like a "new tab" to me, is the one that you'd use if you were just quoting one message, and is the one that you'd use for actually replying to the messages. I think. That's how I do it anyway, although I've not really been using these forums long myself.

> I don't know how I could log in as root, mischievously or otherwise--I've been told about a hundred times that in Ubuntu this can't be done.  I installed a script given in System, Help, System Documentation, Ubuntu Desktop Guide, Configuring Your System, Desktop Tricks, sec. 4.1.10 Open files with administrative privileges from the file manager.  I tried removing the script and rebooting, with no result.  dir with no argument or dir ~ always takes me to /root, not /home/user.  I also disabled automatic log-in and manually logged in as myself, with the same result.

It's certainly possible to log in as root, it's just that the root acount is disabled as an account in its own right by default, and its use is discouraged. The **root@ComputerName:~#** is a big clue that you're logged in as root, though. Not only the user name, but the **#** - if you are logged in as a normal user , that would be a **$**. I don't know how you've logged in as root, but you certainly seem to be, which made me think that you knew more than seems to be the case, and that the home folder question was a trick one.

Is it possible that although you are logged into the desktop environment as a normal user, you've got your terminal to run as root?

I don't know much at all about searching, so I shall leave the rest of your post for someone more competent than I am. Not that I know a huge amount about any of this.

---

### Post by Buck2348 on 2006-11-16
> Sorry if it was me that made you feel that way. I certainly didn't intend to.

It wasn't you at all.  I just get so frustrated when seemingly simple things won't work right.  I quoted you above by copying and pasting, then highlighting the text and clicking the fifteenth icon in the second row in this editing box, with infotip "Wrap >  tags around selected text"  I still can't get anything out of the "forward" icon you mentioned.  I had already tried it since it is labeled something like "Multi-quote this message" but nothing happens when I click on it except the icon changes.  I tried highlighting the text I wanted to quote too.  Would you mind giving me a step-by-step on how you use it?  I'd be grateful.  I can't find any "Help" in the Forum about how to do these things.

[QUOTE]Is it possible that although you are logged into the desktop environment as a normal user, you've got your terminal to run as root?

The menu link to the Terminal is Applications > System Tools > Root Terminal.  Is that normal?  I haven't changed anything there or installed a package since I installed Ubuntu.  When I first start the terminal, it defaults to "root@Dmitri:/home/buck#"  Dmitri is the computer's name and buck is my user name, so it's defaulting to my home folder.  I don't know what's going on.  Is it usual for that line to start with "root@"?  I just noticed that the infotip for the launcher link reads "Opens a terminal as the root user, using gksu to ask for the password."  Do you have to give a password when you open a terminal?  The only password available is mine, which works.

Thank you again for your kind replies.  I hope to hear from you again.

Buck

---

### Post by aidanr on 2006-11-16
normally you  would use Applications->Accessories->Terminal rather than the root terminal in System Tools, it's safer than using a root terminal all the time, you can right click on Applications, Edit Menus and uncheck the root terminal launcher to hide it

---

### Post by CatKiller on 2006-11-16
> **Buck2348 said:**
> It wasn't you at all.  I just get so frustrated when seemingly simple things won't work right.  I quoted you above by copying and pasting, then highlighting the text and clicking the fifteenth icon in the second row in this editing box, with infotip "Wrap "QUOTE" tags around selected text"  I still can't get anything out of the "forward" icon you mentioned.  I had already tried it since it is labeled something like "Multi-quote this message" but nothing happens when I click on it except the icon changes.  I tried highlighting the text I wanted to quote too.  Would you mind giving me a step-by-step on how you use it?  I'd be grateful.  I can't find any "Help" in the Forum about how to do these things.

It's a bit confusing. It took me a while. So this is what I've come up with by trial-and-error:

The box with the yellow blob on it, on the left - that says Reply With Quote in the tooltip now that you mention it - is the one that you would use if you wanted to reply to one post and quote everything that they'd said. You'll probably end up using this one quite a lot. You'll notice, when you use it, that you go to a new page, with the quoted text in the Message box.

The box with the blue blob on it, on the right - that says Quick Reply to this message in the tooltip - is the one that you would use if you wanted to reply to one post but not quote anything in particular. Then you type your message in the box at the bottom of the page. You'll notice, when you use it, that you don't go to a new page, and if you end up foolishly navigating to a different page by mistake, by the time you find your way back to the thread you're replying to the text you've already typed has disappeared. This can be quite frustrating.

The envelope icon, in the middle - that has Multi-Quote This Message in the tooltip - you'll use hardly at all. You'd use this if you wanted to reply to several posts and also quote what was said in them, all at once. The way to use this function is to click on the icons for all but one of the posts that you want to reply to - you'll notice that the icon changes to show that that post is "tagged" (click on the icon again to "untag" that post) - and then click on the Reply With Quote icon for the last post that you want to reply to. You'll notice, when you use it, that you go to a new page, with the quoted text of each of the posts in the Message box.

I'm sure that there is some deterministic ordering scheme for how the quotes are laid out, but I haven't used the function enough to care. I just move the text around if the order's not to my liking.

> The menu link to the Terminal is Applications > System Tools > Root Terminal.  Is that normal?  I haven't changed anything there or installed a package since I installed Ubuntu.  When I first start the terminal, it defaults to "root@Dmitri:/home/buck#"  Dmitri is the computer's name and buck is my user name, so it's defaulting to my home folder.  I don't know what's going on.  Is it usual for that line to start with "root@"?  I just noticed that the infotip for the launcher link reads "Opens a terminal as the root user, using gksu to ask for the password."  Do you have to give a password when you open a terminal?  The only password available is mine, which works.

Ah. No, you don't normally have to type your password to open the Terminal. The Root Terminal does seem to be there for people that don't want to type "sudo" all the time. There should be a normal user Terminal at Applications -> Accessories -> Terminal. You might find these pages
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
to be informative. I **think** that the Root Terminal launcher is the same as the command **gksu gnome-terminal**. **Sudo** (and the graphical variants **gksudo** and **gksu**) is used before a command to say that you want to run that command as the root user. If you have the authority to do so, that's what happens. Those links should tell you more.

You're doing fine, and welcome to the community.

---

### Post by Buck2348 on 2006-11-16
> **CatKiller said:**
> It's a bit confusing. It took me a while. So this is what I've come up with by trial-and-error:


Thank you so much!  I had just figured out by reading your previous post what the "Multi-quote" button is for.  As I said previously, I can quote selected passages by using the button in the toolbar of the reply message box.  The only way I've found to quote and include the user name of the person quoted is click the "Reply with Quote" link and then delete all but the relevant passage in the reply message box.  I kept looking for a way to quote just a passage by highlighting it and clicking "Reply With Quote."  I notice some multiple quotes in a message all have the "Originally Posted by ..." tag on them.  How do they do that?

Well, I see now of course why I was in a Root Terminal.  Do all installations of Dapper have the Root Terminal available in the System Tools menu, do you know?  If not I'd be curious to know why I have it.

Thank you again very much for your help.  Now if I can get my Search function working I'll be content for a while.

Buck

---

### Post by PilotJLR on 2006-11-16
> **Buck2348 said:**
> 
Thank you again very much for your help.  Now if I can get my Search function working I'll be content for a while.

Buck

If you haven't already, follow the directions listed here:
[https://help.ubuntu.com/community/Beagle](https://help.ubuntu.com/community/Beagle)

What you basically need to do is install beagle with a "sudo apt-get install beagle".
Then, still at a command prompt, and NOT AS ROOT, type "beagled".
Then, add the search applet to the the top or bottom panel by right-clicking on the panel, then "Add to Panel," then "Application Launcher," then "Accessories," and finally drag the Search icon (magnifying glass) onto the panel.
This applet is what lets you use beagle.

Lastly, click System | Preferences | Session, then click the "Startup Programs" tab, then click add and type command "beagled". This ensure it starts itself when you login later.
It will take a little while to index everything, so give it some time to work. Once it's caught up, you won't even notice it indexing new content.

---

### Post by CatKiller on 2006-11-16
> **Buck2348 said:**
> Well, I see now of course why I was in a Root Terminal.  Do all installations of Dapper have the Root Terminal available in the System Tools menu, do you know?  If not I'd be curious to know why I have it.

I don't know, I'm afraid. My Dapper's an upgrade from Breezy. I **think** it was there by default in Hoary, but it's been so long since I saw a default menu that I really couldn't say. The menu entry is there in each case, it's just a question of whether it's enabled. Right-click on the menu and select Edit Menus to see what I mean. As aidanr says, you can untick the boxes to have any of the entries not show up in the menu. If the sub-menus don't have any entries shown in them, then the sub-menus aren't shown either. Which is nice.

---

### Post by Buck2348 on 2006-11-16
> **PilotJLR said:**
> If you haven't already, follow the directions listed here:
[https://help.ubuntu.com/community/Beagle](https://help.ubuntu.com/community/Beagle)




Thanks, I appreciate your help.

I can't seem to get Beagle to do its indexing without manually specifying each subdirectory of File System under menu: Search > Preferences > Indexing > Add.  In the left pane I click on File System but the buttons at the bottom for +Add and -Remove are both grayed out so the only way I can add search paths is to double-click on File System and then select and add each subfolder one at a time.  This works but its tedious, and I don't know why it won't automatically index my system. I'm trying to find a way to do it from the command line, but that's chancy for me.

Also I don't see any way for doing a search for files or folders alone--the list that drops down from menu Search, starting with Everything seems to include everything but that.

Thanks again.  How long have you been flying a cubicle?

Buck

Later--Beagle seems to be indexing my file system now, but as of yet it never finds any files--only folders.  When you say it takes a little while to do the indexing, do you mean several minutes, several hours, or longer yet?

---

