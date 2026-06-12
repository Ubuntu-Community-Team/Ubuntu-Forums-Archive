---
title: "Good, fast file transfer"
date: 2007-03-29
forum: Apple Intel Users
---

### Post by brad1150 on 2007-03-29
What is a good and fast way i can upload files to my ubuntu server. I have to remote desktop to the server, and instead of having to upload stuff on my computer to a website, then download it at teh server, i would just liek to directly transfer the files. the server is behind a router, but I can port forward it.


EDIT: BTW could a mod please move this to networking or general please, i just realized I posted in the wrong category.

---

### Post by 1/0 on 2007-03-29
Personally, I would install a ssh server. [This]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#SSH_Server") on is a good [guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#SSH_Server") on how to setup a ssh server. 

Otherwise you could install an FTP server but those are not encrypted. Its faster though. 

For both: USE NON STANDARD PORTS. Don't use port 21. Choose a port over 10000 and you'll be rid of many attacks.

PS You can use gFTP for file transfer if you want a GUI.

---

### Post by brad1150 on 2007-03-29
I would like something easy to set up with a  guii, as i am still a newb to ubuntu. All it is going to be used for is uploading files to my "garry's mod" server, as i have a  lot and it is a pain to install the mods using VNC.

---

### Post by devnulljp on 2007-03-29
[QUOTE=brad1150;2372687]What is a good and fast way i can upload files to my ubuntu server. I have to remote desktop to the server, and instead of having to upload stuff on my computer to a website, then download it at teh server, i would just liek to directly transfer the files. the server is behind a router, but I can port forward it.

scp or rsync will do what you want, and are more secure than setting up an ftp server just to move files back & forth.

syntax:

From remote box to your home server:
```
scp file1 file2 file3 username@home.server:directory/where/you/want/to/save
```
To copy a whole directory, use -r
```
scp -r directory username@home.server:directory/where/you/want/to/save
```

rsync is good for incremental copies of directory structures so you don't have to copy everything again if you've only made some small changes on the remote machine
```
rsync [OPTION]... SRC [SRC]... [USER@]HOST:DEST

rsync -avz foo:src/bar /data/tmp

```
From the man page:
       This would recursively transfer all files from the directory src/bar on
       the machine foo into the /data/tmp/bar directory on the local  machine.
       The  files  are  transferred in “archive” mode, which ensures that sym&#8208;
       bolic links, devices, attributes,  permissions,  ownerships,  etc.  are
       preserved  in  the transfer.  Additionally, compression will be used to
       reduce the size of data portions of the transfer.

Try man scp and man rsync for more info

---

### Post by brad1150 on 2007-03-29
BTW i am using windows on the pc the files are on. Will this still work?

---

### Post by cyberdork33 on 2007-03-29
WinSCP will allow you to transfer files via SCP from windows.

---

### Post by 1/0 on 2007-03-30
I second that WinSCP from a Windoze computer. The equivalent to WinSCP for Linux would, for instance, be gFTP.

As I said before you'll need to set up a SSH server on the file server in order to connect via the SSH protocol. Remember to switch port in /etc/ssh/sshd_config (change: Port 22).

---

### Post by cyberdork33 on 2007-03-30
actually there are several FTP clients that support SFTP or SCP... WinSCP is one of the best though, because it is just a single binary. I keep WinSCP, PuTTY, and TightVNC Viewer on a flashdrive in my pocket at all times.

---

### Post by brad1150 on 2007-04-22
I'm just going to use Proftpd. it simple and I already have it installed.

---

### Post by TekNullOG on 2007-05-15
Thanks for the post. I was having syntax problems with scp and this really helped. I wanted my file transfers to be independent from the gui so that if I need to do Ctrl+Alt+Backspace it won't terminate my transfer.

Can't wait to get RSync working.

Man linux is fun!

---

### Post by Gen2ly on 2007-05-16
devnulljp

thanks for the info in rsync I'd been thinking about making incremental backups of my home directory.  So now I have information to work with.

could you explain the

```
foo:src/bar
```

---

### Post by TekNullOG on 2007-05-16
I forgot to mention that to run a file transfer in the background, you need to use **screen**.

You can learn more about this command [http://www.bangmoney.org/presentations/screen.html]("http://www.bangmoney.org/presentations/screen.html")

You can easily do large backups and then close your shell and log out of your session without worrying about things disconnecting.

---

