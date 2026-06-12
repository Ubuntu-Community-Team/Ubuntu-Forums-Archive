---
title: "Used WinSCP and Pagent in Windows"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Yazaaab on 2007-05-04
I am new to Ubuntu and I am having trouble figuring out how to replace these two products from my windows machine. WinSCP and Pagent.  I have been sent a .ppk file that I need to load so that I can FTP?  Any suggestions on how I can get this to work in Ubuntu as I am really liking so far a would like to get totally away from windows.

---

### Post by dannyboy79 on 2007-05-04
ok, well, they sent you a putty key. it sounds like you want to download files from an ssh server not a ftp server because WINSCP is a gui to download stuff from an ssh server. Pagaent merely organized your ssh keys in windows I believe. so what you'll want to do first is convert your .ppk file using puttygen so that it's a real ssh key file not a putty key file. puttygen is a windows program and is really easy to use. it'll be self explanatory. I am not aware of what to use in linux to convert a putty key file into a ssh key file.

then you will want to use gftp in ssh mode (changing to scp or ssh mode can be  done by looking in the upper right corner of gftp) to get a similar gui for downloading stuff securely. that's it. good luck.

---

### Post by Yazaaab on 2007-05-05
> **dannyboy79 said:**
> ok, well, they sent you a putty key. it sounds like you want to download files from an ssh server not a ftp server because WINSCP is a gui to download stuff from an ssh server. Pagaent merely organized your ssh keys in windows I believe. so what you'll want to do first is convert your .ppk file using puttygen so that it's a real ssh key file not a putty key file. puttygen is a windows program and is really easy to use. it'll be self explanatory. I am not aware of what to use in linux to convert a putty key file into a ssh key file.

then you will want to use gftp in ssh mode (changing to scp or ssh mode can be  done by looking in the upper right corner of gftp) to get a similar gui for downloading stuff securely. that's it. good luck.

I do want to download from a SSH server, they refer to it as FTP so I have a started to make the same mistake.  Thanks for the answer.  Do you think I could I could use Wine to run puttygen?  The only reason I ask is I am trying to prove to my boss that we can work in a Linux world without having to go to Windows for anything and so far I am have been successful using Wine and Crossover for Apps.   So if I could convert with out having to use windows, that would be super.

Thanks,

---

### Post by tr333 on 2007-05-05
the actual protocol you are using is sftp, which is a combination of normal ftp and the secure data transmission of the ssh protocol.

---

### Post by dannyboy79 on 2007-05-07
> **Yazaaab said:**
> I do want to download from a SSH server, they refer to it as FTP so I have a started to make the same mistake.  Thanks for the answer.  Do you think I could I could use Wine to run puttygen?  The only reason I ask is I am trying to prove to my boss that we can work in a Linux world without having to go to Windows for anything and so far I am have been successful using Wine and Crossover for Apps.   So if I could convert with out having to use windows, that would be super.

Thanks,

I haven't used puttygen in wine so I could tell ya. gogle it or look in the winedb (wine databse of apps that work) good luck

---

### Post by rich.bradshaw on 2007-05-07
I have a weird feeling (prob wrong!) that there is a version of this compiled for Ubuntu already - try looking in synaptic...

Once you have it set up, you can use Places/Connect to server to add the server permanently so you can drag and drop files to it etc without problems. It works brilliantly - one of the main reasons I use Linux.

---

