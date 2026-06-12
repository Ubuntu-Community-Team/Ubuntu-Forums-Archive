---
title: "Rar Archive and others"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by clapton on 2008-03-03
Hello people!

I'm not a really noob, but sometimes I've got beginner questions.
How can I set password at archives rar?
Or other, like 7zip or zip?

Is there a way to set with nautillus?
Thank you

---

### Post by Roanoke on 2008-03-04
I'm sorry, but I have no idea what you are saying, but I'm going to go out on a limb here and improvise. In the future, please write coherently.

I'm guessing that you want to encrypt a file. There are several ways to do this. If you are using KDE, there is a utility called "KGPG" which will encrypt any file/folder you give it. Later, if you give it the password that you set up, it will decrypt it.

I you are using GNOME, then you can download kgpg from the commandline like so:

```
sudo apt-get kgpg
```

After which you will be asked for your password, you will enter it, and the package will install. However, should you not want to install a kde app on a gnome system, use gpg from the commandline like so:

```
gpg --gen-key
```

That will make a key. Answer the questions, then type:

```
gpg --encrypt FILENAME
```

Replacing filename with the name of the file to be encrypted.

---

### Post by fenian on 2008-03-04
First install the rar program,open a terminal and enter...

> sudo apt-get install rar

Next to compress a folder with password protection (for this example I am compressing a folder named test that is located on the Desktop) ,open a terminal and enter

> rar a ~/Desktop/test  -p

you will be prompted to enter and confirm a password for the archive after you do so the folder should be compressed with password protection.

---

### Post by clapton on 2008-03-04
Sorry people, I'm portuguese and I write this post to late.

Yes I wanna manage easilly archive files.
Set password, split, add to archive without terminal.

---

### Post by Roanoke on 2008-03-04
Why would you want to do it without the terminal?

---

### Post by zerhacke on 2008-03-04
What's it matter, Roanoke?  It's his machine, let him give his own stipulations.  It doesn't affect you, does it?

---

### Post by TenPlus1 on 2008-03-04
Use the Archive Manager to create your archive and in the Edit menu you will see an option to set a Password before adding files to be encrypted...

---

### Post by stchman on 2008-03-04
> **clapton said:**
> Hello people!

I'm not a really noob, but sometimes I've got beginner questions.
How can I set password at archives rar?
Or other, like 7zip or zip?

Is there a way to set with nautillus?
Thank you

I believe that Archive Manager allows you to create password protected archives.

---

