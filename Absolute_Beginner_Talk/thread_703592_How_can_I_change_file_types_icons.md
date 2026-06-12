---
title: "How can I change file types icons?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Tryfon on 2008-02-21
Hi, I'm new in Linux but things aren't so difficult as I thought they'd be. Still I have this problem. I want to set the icon for all my torrent files to be the cute icon with the blue frog that azureus provides, but I can't find how to do that. Right now the default icon is a white sheet folded on the one edge.
Any ideas?

---

### Post by banewman on 2008-02-21
As the torrent file is a text file you would need to change all text files to have that icon.
Is that something you want to do?

---

### Post by Tryfon on 2008-02-22
But isn't the ending that characterizes a file? It has a .torrent ending not .txt

---

### Post by kaiju on 2008-02-23
i think what banewman means is that linux looks at the mime type of files rather then their extensions, when finding out their filetype. (Take a quick look here: [http://www.novell.com/coolsolutions/tip/16269.html]("http://www.novell.com/coolsolutions/tip/16269.html"))

however, it seems that (at least in thunar) filetype icons are displayed depending on the extension of the file.
all i'm saying is that i don't know the answer to your original question, but i think that what you want is possible.

---

### Post by chewearn on 2008-02-23
I'm also a newbie of this topic; but after searching around and experimenting, this worked immediately on my ubuntu PC; hope it does the same with yours:

```
sudo cp <icon-file-name> /usr/share/icons/application-x-bittorrent.png
sudo chmod 644 /usr/share/icons/application-x-bittorrent.png
```Replace <icon-file-name> with the icon file you want to use.
I found that you can use png or jpg, but not ico file.  But the file name in "/usr/share/icons" must be png extension.

---

### Post by Tryfon on 2008-02-24
Could you please explain me the command, especially the second one, because I might want to do that again for a different file and because I have uninstalled the default torrent client and installed Azureus?

---

### Post by chewearn on 2008-02-24
First, I corrected a typo for the second command; it should include the directory path as well.

Explanation for the commands:
First command simply copy your icon file to the location where the system icons are stored.  For some reasons (I don't know enough about the inner working of ubuntu to be able to explain why), once you have that icon file in that exact location, plus with that exact filename of application-x-bittorent.png, the ubuntu gui automatically picks up the icon file and associate it as the icon for torrent file.

The second command change the permission of the file to be read+write for owner (root in this case), but readonly for everyone else.  The second command might not be necessary, if the file already has the correct permission.

---

### Post by kaiju on 2008-02-24
> **AstalaVista said:**
> 
```
sudo cp <icon-file-name> /usr/share/icons/application-x-bittorrent.png
sudo chmod 644 application-x-bittorrent.png
```

the first command given by AstalaVista copies the icon file you wish to use into the system-wide icon directory and gives it a standard name. you have to use sudo because /usr/share/icons/ is only writable with root access.

the second command changes the permissions of the newly copied file so that all users can read it (this way apps started with any user's permissions can display the icon).

to better understand why you are using the value 664, you can take a look at [http://www.zzee.com/solutions/linux-permissions.shtml#numeric](http://www.zzee.com/solutions/linux-permissions.shtml#numeric).

---

### Post by kooolrock on 2008-02-24
> **Tryfon said:**
> Hi, I'm new in Linux but things aren't so difficult as I thought they'd be. Still I have this problem. I want to set the icon for all my torrent files to be the cute icon with the blue frog that azureus provides, but I can't find how to do that. Right now the default icon is a white sheet folded on the one edge.
Any ideas?
u r a beginner and u r already yawning????!!!:):D

---

### Post by zeigfried on 2008-07-16
I know this post is old but since it helped me I'll give my contribution.

The icon file name works because the torrent mime type is detailed on the gnome shared mime database.
There is a nice applied tutorial that shows how to create new mime types in [http://adrianus.wordpress.com/2007/02/07/howto-add-new-mime-types-and-icon-for-visio-document-in-ubuntu/]("http://adrianus.wordpress.com/2007/02/07/howto-add-new-mime-types-and-icon-for-visio-document-in-ubuntu/").

Wouldn't it be nice to have an easy interface to handle mime types on gnome?

---

