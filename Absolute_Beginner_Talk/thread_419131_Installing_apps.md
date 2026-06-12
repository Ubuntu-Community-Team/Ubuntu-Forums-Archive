---
title: "Installing apps"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by DeadlyAura on 2007-04-22
Basically, I'm a n00bie to Ubuntu.

I'm using Kubuntu 6.06 and can't figure out how to get my programs to run.

I was able to install Firefox and Thunderbird via apt-get, but can't install any programs from files located on the PC itself.

The program is FAH504-Linux.exe. I followed the install instructions.

```
chmod +x FAH504-Linux.exe
```

And received the error:

```
chomd: cannot access 'FAH504-Linux.exe': No such file or directory.
```

I even tried prefacing the command with sudo just to see if that changed anything, but still nothing.

So I downloaded a tar of the app thinking that might work.

```
tar -xvzf fah_install-200604.tar.gz
```

And received this message:

```
tar: 'fah_install-200604.tar.gz' Cannot Open: No such file or directory
tar: Error is not recoverable: Exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

Does anyone know what I am doing wrong?

I'm sorry for the trouble and the fact that I'm a n00bie. :)

---

### Post by jfinkels on 2007-04-22
Make sure you are in the right directory when trying to run the executable file, and when trying to extract the files from the .tar.gz archive. For example, if you download a file to the "Desktop" folder, it will be in "/home/*yourusername*/Desktop". To do anything to that file you either have to use its full directory path or change your current working directory to that directory. Let me show you.

If your username is "deadlyaura", type the following in the terminal to change your directory:
```

cd /home/deadlyaura/Desktop

```
Type the following to list the contents of the current folder:
```

ls

```
(that's the letter L and the letter S)

Then do whatever to the file by typing whatever program you want to run on the file:
```

chmod +x FAH504-Linux.exe
./FAH504-Linux.exe

```

---

### Post by raja on 2007-04-22
Are you in the folder that contains the exe? The error message seems to indicate that this is not the case. You can list the contents of the folder with ```
ls
``` to make sure that your working folder has the file before you try to make it executable.
Once you chmod +x, you can run it with ```
./FAH504-Linux.exe
```

---

### Post by DeadlyAura on 2007-04-22
jfinkels, you are my freaking hero. You were right, I was in deadly@deadly-desktop:~$. This seemed to me (being a new Linux user) to be the right folder. Apparently, after changing the directory, I was proven wrong.

Apparently it should have read deadly@deadly-desktop:~/Deskop$.

Thanks a bunch, I appreciate the quick response.

---

### Post by jfinkels on 2007-04-22
> **DeadlyAura said:**
> jfinkels, you are my freaking hero. You were right, I was in deadly@deadly-desktop:~$. This seemed to me (being a new Linux user) to be the right folder. Apparently, after changing the directory, I was proven wrong.

Apparently it should have read deadly@deadly-desktop:~/Deskop$.

Thanks a bunch, I appreciate the quick response.

No probs, just keep posting in the forums and you'll get great help!

By the way, here's a link to a post I made in a different thread, describing the prompt at the terminal ([http://ubuntuforums.org/showpost.php?p=2423564&postcount=21)](http://ubuntuforums.org/showpost.php?p=2423564&postcount=21)).

Check out [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) for some great intro material :)

---

