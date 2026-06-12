---
title: "How to change AND KEEP chmod rights?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-04-24
Hi,

I have a website for which I have to use ftp programs regularly (for updating). Now I recently switched to ubuntu and I want to change everything to ubuntu. I have an external harddrive (by western digital) and i made one ext3 partition on it. Now I gave 770 rights to that partition and also clicked "apply to all subfolders and files" (or something similar..) by logging in as root. I gave the second 7 to the group 'ricam' which is my username which I normally log in with.

However, when I now want to download something to it, it says either that the folder doesn't exist, or that I don't have the rights to do it.

I just want to be able to download things (my whole website) change them, and upload them again without any right changing.

What do I need to do?

---

### Post by alanphil on 2007-04-24
How is your external hard drive connected to the system? USB? Firewire? 

Is the hard drive setup to auto-mount on Ubuntu?

---

### Post by kramer65 on 2007-04-24
It is connected trough firewire. I don't have a clue about automatic mounting or something.. what is that? How can I check it?

In the meantime I got a bit further. I changed the permissions to 777 and now I can access and change things. When I now download things they keep the chmod they had on the server before as well. 
But is it safe to have a 777 chmod?

And I have a new problem now as well. When I download a big folder from my website with a lot of subfolders and different files (zen-cart folder) Gftp simply closes after a while. 

Is it possible that Gftp can't handle this? I thought that that would not be a problem..

---

### Post by alanphil on 2007-04-24
>But is it safe to have a 777 chmod?
That depends on who will have access to this drive. Is this HD for private development and testing? Or are you putting this system on the Internet to serve web pages? If it's just for local development on your private network there probably isn't too much danger in this.

I've used gFTP to move huge amounts of data and have never seen it close before finishing. Are you using the secure sFTP protocol to connect to the remote server? Is the remote server timing out?

---

### Post by kramer65 on 2007-04-24
As far as I know I don't use sFTP..

I don't really know why it is either. It starts by indexing the folders or something. At least, on the left top of the screen I see something counting, and when it counted like 400 folders it suddenly stops. I really dont know why..?

---

### Post by alanphil on 2007-04-24
In gFTP, in the upper right there is a pulldown menu where you select the protocol. I think it defaults to FTP, but I usually use sFTP. 

Try transferring one or two files and see if that works as expected.

---

### Post by kramer65 on 2007-04-24
I only have the options of

HTTP
Local
SSH2
FSP

Which one would it be?

---

