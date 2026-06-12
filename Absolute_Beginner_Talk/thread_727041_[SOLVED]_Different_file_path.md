---
title: "[SOLVED] Different file path"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by TzaB on 2008-03-17
Hello all, i am using Ubuntu and Windows XP on the same machine and i want to ask a question.

I have access on the files that are in the partition of Windows from Ubuntu, but the paths of the files are differents. For example, if i want to open the folder "My Documents" from the C:/ when i am in Windows i follow the directory 

C:/Documents and Setting/tzab/My Documents

When i am with Ubuntu and i open 

Computer/Local Disk/Documents and Settings/tzab/

the folder "My Documents" is not exists. Why? Can someone explain it please?

Thanks for reading

---

### Post by jken146 on 2008-03-17
Windows is funny like this.  Boot up into Windows, right click on your My Documents icon and click on Properties.  As far as I remember, there is an option to move My Documents to a different location, so look there for the path to where it actually is.

---

### Post by TzaB on 2008-03-17
I did it and in properties there is the same path (C:/Documents and Settings/tzab).
Actually, I created this thread because i cant understand how it is possble to be a problem like this. Am i the only one that has this problem?

I will tranfer "My Documents" to a path that i will be able to see from Ubuntu, for example to the "Program Files" folder but i want to know why somethings are happening when i have the chance to learn them.

Thanks for your advice dude.

---

### Post by stchman on 2008-03-17
> **TzaB said:**
> Hello all, i am using Ubuntu and Windows XP on the same machine and i want to ask a question.

I have access on the files that are in the partition of Windows from Ubuntu, but the paths of the files are differents. For example, if i want to open the folder "My Documents" from the C:/ when i am in Windows i follow the directory 

C:/Documents and Setting/tzab/My Documents

When i am with Ubuntu and i open 

Computer/Local Disk/Documents and Settings/tzab/

the folder "My Documents" is not exists. Why? Can someone explain it please?

Thanks for reading

The My Documents is located in your profile in Windows.  Windows puts a shortcut on your desktop.

My Documents equates to this in Windows:

C:\Documents and Settings\<Windows user name>\My Documents

In Ubuntu it should equate to this:

/<mount point>/Documents and Settings/<Windows user name>/My Documents

My Documents is analogous to home in Linux.

---

### Post by natirips on 2008-03-17
If your using NTFS (file system) on windows, your "My Documents" folder might be "protected". I haven't used a windows machine in months now, but if I recall correctly, you can go to "c:\documents and settings\<user name>\", then right-click your "My Documents" folder, then properties, and check the situation under Security tab (if it exists)(try adding user "Everyone" and give it read permissions).

Note: I assume you're using XP, although it shouldn't be much different if it were some other version.

---

### Post by TzaB on 2008-03-17
Yes, you were right. The folder "My Documents" was "protected". I did what you said but yet i cant see the Folder "My Documents" from Ubuntu partition :/

I cut-paste the folder "My Documents" into Program Files that i am able to view all the files that exists there, but i cant see the folder again.

Thanks for the suggestions all. If someone have the same problem or know something that he thinks that will help, please post a reply.

---

### Post by TzaB on 2008-03-17
Hm i found it... I am sorry guys for the time that i waste you because i didnt mention that  the Windows XP are in Greek language and the folder "My Documents" is "&#932;&#945; &#941;&#947;&#947;&#961;&#945;&#966;&#940; &#956;&#959;&#965;" in greek language.
I translated the folder in english in order to be understandable to people that dont know greek.

I did not know that Ubuntu cant appear folders that are in other languages except english.

So when i renamed the folder "&#932;&#945; &#941;&#947;&#947;&#961;&#945;&#966;&#940; &#956;&#959;&#965;" to an english word, i was able to view it...

Thanks for reading the whole post and shared your suggestions.

---

