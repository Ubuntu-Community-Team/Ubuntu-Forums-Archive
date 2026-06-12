---
title: "Using SSHFS to mount remote drive via SFTP help needed"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by will m. on 2007-02-02
I am trying to mount a remote drive via SFTP using SSHFS.  To do this I am following the instructions below.

```
sshfs has the advantage over a KIOslave or GnomeVFS that any program can use it. For instance, in Kubuntu Amarok wasn't able to play my remote music through fish:/ but worked fine using sshfs.

1) Install the software
sudo apt-get install sshfs

2) Add fuse to /etc/modules
sudo nano /etc/modules

3) Add yourself to the 'fuse' group, then log out and log in again.
sudo adduser your-username fuse

4) Create a mountpoint and give yourself ownership
sudo mkdir /media/mount-name
sudo chown your-username /media/mount-name

5) Mount the filesystem
sshfs remote-system-name:/remote-folder /media/mount-name

6) Unmount the filesystem
fusermount -u /media/mount-name

Directions taken from http://ubuntu.wordpress.com/2005/10/...m-using-sshfs/ More info on sshfs is available at http://fuse.sourceforge.net/sshfs.html

I've run into a strange problem on two Kubuntu machines where, after using sshfs, you're unable to unlock your own computer. Logging in works fine, but you can't return from a password-protected screensaver. My solution was to start a new session, change my password, then return to the old session and use the new password to unlock it.
```

The instructions seem to be working, all the necessary modules for SSHFS are installed, I seem to be talking to the SFTP remote site.  However, when I input these the response I get is
```

ubunutu_username@remotehost's password: 

```
I expect to be required to provide my remotehost username and password (Windows Active Directory) but it seems that SSHFS is using my Ubuntu login and password and assuming that some match exists on the remotehost.  Is there something I can do to specify the difference between the two of these?

I'm so close to being able to sync up my files remotely!  I've really looked around, spoken with my workplace's network admin and found that the support that SSHFS provides is what I need (I think ; )).

Does anyone know how to clarify this problem?

Thanks,

Will M.

---

### Post by kingmonkey on 2007-02-02
You can sync files remotely using rsync

---

### Post by will m. on 2007-02-02
I have tried Rsync, among others, but it does not seem to allow for SFTP.  Does it in fact allow for this?

Will M.

---

### Post by steve.horsley on 2007-02-02
I've never mounted an SFTP drive, but if it's good enough for you, you can access one in nautilus (for drag/drop file access) by typing in a URL like "ssh://steve@1.2.3.4". You can even make a launcher with a command like "nautilus ssh://steve@1.2.3.4".

---

### Post by will m. on 2007-02-02
Thanks, Steve.

I have tried this and it has been semi-successful.  I am connecting to my workplace's servers and I can transfer files.  The strange thing is that the files aren't actually visible in the directory when I am accessing the files through Windows (or through other applications that allow for SFTP connections like Filezilla).  Another anomaly is that I can't see any of the files in the directory from Nautilus. 

I would strongly prefer to use Nautilus for this purpose but can't see doing so under this condition.

Any thoughts on why the files aren't visible?

Will M.

---

### Post by kebes on 2007-02-02
> **will m. said:**
> I have tried Rsync, among others, but it does not seem to allow for SFTP.  Does it in fact allow for this?


Yes you can tunnel [rysnc ]("http://www.die.net/doc/linux/man/man1/rsync.1.html") through ssh quite easily. (sftp is just file transfer using ssh.) All you can to do is add "ssh" to the rsync command. For instance, if you want to copy files from "/home/user/dir/" to the remote server "server.com" using the account "username", you'd go:

rsync -rlptD --delete -e ssh /home/user/dir/ [email]username@server.com[/email]:/home/username/dircopy/

The -rlptD options are typical for doing a sync, and the --delete tells it to delete a file on the remote side if it no longer exists on the local side. (Remove that option if you don't need it.)


rsync is very efficient because it only transfers files that have changed, so doing backups can be alot faster.

---

### Post by will m. on 2007-02-02
Hallelujah!

I had the directory WRONG this entire time.  Here's what happened...

In our shop we have a directory /HOME that is where each Active Directory user has space set aside under their USERNAME.  So the directory /HOME/USERNAME is what I had in my request in Nautilus that I quoted earlier.

ssh://username@domain:port/HOME/USERNAME

And when I used that I connected but couldn't see a thing.

Then, just after your previous post I tried looking around a bit in the directory that I had access to.

ssh://username@domain:port/HOME/

The above request worked PERFECT!  All this time the username was sufficient to tell the Windows server which directory of /HOME to access.

I was soo frustrated by this.  I am so glad to have solved this, finally.

Thank You for your help!

Will M.

---

### Post by kebes on 2007-02-02
> **will m. said:**
> The strange thing is that the files aren't actually visible in the directory when I am accessing the files through Windows (or through other applications that allow for SFTP connections like Filezilla).

In what modes *can* you see the files, then? (How do you know they've been transferred if they don't show up in Windows or via SFTP?) If you can see them via ssh, what happens when you go "ls -laF"? Is it possible that the permissions on the files you transferred are set such that others cannot see them?


Edit: nevermind! Looks like you got it working!

---

### Post by will m. on 2007-02-02
Thanks, Kebes.  I will try this too as it might be a more efficient way to accomplish this than having a permanently mounted drive.  Actually, in cases of network outage on my part or at my workplace it would be essential to have this worked out.

Thank you very much.

Will M.

---

### Post by Old Jimma on 2007-04-04
Hi Ubuntu-ers:

I found Will M's Jan 2007 instructions spot-on, ie, they worked perfectly. 

Also, I tried using

sshfs user$ipaddress:/folder /mountpoint

That worked even bettter for me, where ipaddress is the ipaddress returned from ifconfig on user's machine.

There are 3 more things that would be very nice to add to Will's instructions:

1. how to mount the /folder automatically on startup,
2. how to improve performance (it is a little slow), and
3. how to make sure that the user will not overwrite or destroy the data in /folder

Many, many thanks to Will for giving instructions that actually work.

Sincerely,
Phil Smith
Duluth, GA

---

