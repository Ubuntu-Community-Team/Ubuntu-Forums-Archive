---
title: "Can't see network files in mounted share."
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by skullosorus on 2007-03-06
I can mount my network shares (folders) from my Windows 2003 server, but can not see the contents. I'm using LinNeighborhood on DreamLinux. When I used FC-5, I could mount-see-use all files on server. I beieve I go something configured wrong. I know it mounted cause I can open the folder with my File Manager but nothing is in their. I'm cornfused.........................

---

### Post by dstew on 2007-03-06
My big nightmare with not seeing shared files in a mounted share (using samba over a VPN connection) was caused by a single unusual character in one file name in the folder. When samba was getting the file names for a directory display, the unusual character caused it to fail. The character was a Tm (trademark) character.

There are other possibilities, such as proper permissions, but those have been well-covered elsewhere. I can only add my Tm character problem to the mix.

---

### Post by skullosorus on 2007-03-06
I'll take anything at this point. To see if what you proposed could be the issue, I created a 'Test' share with only Linux based files on my server. I mounted it, but still no files are visible. At first I thought it could have been a login\rights issue, so I also logged into my server with admin account. I am very new to forums and also very thankfull for the help that I have recieved.

---

### Post by dstew on 2007-03-06
The permissions problem has to do with making sure the mounted share has the permissions for the current user. If you mount a share as root, but look at it as user, you might not see files. I only remember that with samba, I had to put in my linux user id and group id as a mount option (sudo smbmount //server/share ~/Windows_disk -o uid=donn,gid=donn) or something like that (I am not at my linux system at present). If the share is mounted, it is probably not an issue on the Windows side, but on the linux side. But I am no expert here.

---

### Post by skullosorus on 2007-03-06
Question: If I open a terminal, log in as root, cd to the network share and use ls to view contents, should I be able to see my files then regarless of user based permissions? The reason I ask is I did this and still could not see anything even as root. I honestly believe its a permission issue just like you said and I've got something hosed up. I cheated and used my File manager to view permissions (I've really been trying to use just command line) and (at the top it says I'm 'using root account' with a red banner) it says that my user has read only permissions. Also, and I failed to mention from the get go, in the Mount Dialog box for LinNeighborhood, even though I enter the user name and password - it will not mount and comes back with an error saying 'SMB signing is mandatoryand we have disabled it' (it will let me view the available Network shares though). At this point I have to use 'Mount as Root' and use root authenication.I'm lost but patient.

---

### Post by dstew on 2007-03-07
I did some poking around. LinNeighborhood is a front end for Samba. If your server uses Microsoft 2003 software, the server requires a security setting (signing) that Samba cannot provide. You will not be able to mount the share unless you use the newer cifs client. You should still be able to view files on the share using samba client (smbclient). See this thread:
[http://www.openfree.org/forums/showthread.php?t=215](http://www.openfree.org/forums/showthread.php?t=215)

---

### Post by skullosorus on 2007-03-08
Sorry it took me a while to get back - honey do list I had to complete. All I can say is thank you very much for your help and the link. Everything is pefect now. Thank you again.

---

