---
title: "Ubuntu Server 6.06 LTS setup"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by fireman52 on 2007-06-28
I am new to server management, and am trying to set up an NFS server with Ubuntu 6.06 LTS Server.  I have it all installed, but when I try to add hosts by editing the exports file all I get is the message "Operation Not Permitted" when I try to access the file.  

I have tried accessing other files as well, with the same result.  Also, when I try to use the sudo command I am given the same message.  I remember seeing somewhere that this server edition sets you up as a user, not root for your protection, but I am at a loss as to how to get anywhere.  I have searched forums, Ubuntu documentation, etc.  

Any help will be greatly appreciated.

---

### Post by fireman52 on 2007-07-03
well I got my own answer.

After a ton of searching, I found that to edit this file you have to be logged in as root.  And tehn after a bit more searching I found that in order to log in as root you have to sert up a password.

     Enter: [COLOR="Blue"]sudo passwd root[/COLOR]

This will enable you to enter a password, hit enter and reenter the password hit enter again and you are all set.

Now after you log in to the server you enter: su then hit the enter key and you will have to enter the password.  This gets you into root.

To go about editing files and directories, first enter: [COLOR="Blue"]cd /[/COLOR]
This gets you to the root directory and you can do: [COLOR="Blue"]cd /(directory name)[/COLOR] to get you to a directory within root.  If you don't know what the directories are within root 
enter: [COLOR="Blue"]ls[/COLOR]

This gives you all the directories in root.

To view the contents of a directory enter: [COLOR="Blue"]ls (directory name)[/COLOR] and this will list them.

If there are too many entries to view on one page enter: [COLOR="Blue"]ls | less (directory name)[/COLOR]

This will give you one page at a time.  Hitting enter will advance one line at a time, page down or the space bar will go to the next page. 

At the end hit "q" to go back to the prompt

This is my little tutorial, what I have learned so far.

If Ubuntu and Linux is to be better acceated, better instructions are necessary.  The searching and trial and error would turn off the casual user.  I know I am workin gon a server, but this goes mostly for the desktop editions.  Most users don't have the knowledge or patience to go through all this just to use their computer

---

