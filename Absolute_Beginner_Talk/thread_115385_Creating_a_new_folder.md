---
title: "Creating a new folder"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-01-10
How do I do this in Nautilus?

The option is grayed out.

Also what is the command if I was to do this in terminal?

I see i can do it in home but no-where else?

---

### Post by paulmilliken on 2006-01-10
"mkdir foldername" will do the trick in a terminal.  Type "man mkdir" for more details.

Paul

---

### Post by chimera on 2006-01-10
you only have write perrimision for your home folder

and the command is mkdir

and if you're doing it outside of your home folder, you have to become superuser before you can make a folder, therefore:

```

sudo mkdir name

```

(name is the name of the folder)

you'll be prompted for your user password, which you'll have to provide.

---

### Post by _simon_ on 2006-01-10
thanks guys :)

---

### Post by Omnios on 2006-01-10
> From: [http://www.linuxdevcenter.com]("http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=m/mkdir")
mkdir

mkdir [options] directories

Create one or more directories. You must have write permission in the parent directory in order to create a directory. See also rmdir. The default mode of the new directory is 0777, modified by the system or user's umask.

 For a root owned file use sudo

 cd to the directory you want to make the file or include the path to file + new filename ex. mkdir  /home/my_name/new_file_name
```
sudo mkdir filename
```

Edit: you Beat me to it lol.

 CHeck out Know your terminal commands in my signature

---

### Post by winlux on 2006-01-10
Usually you would not want to be able to create files or folders in your system dirs. That could lead to security holes and make it easier for rootkits being installed. Although if you really need to you can change the owner of the folders using the chown command. You need to be careful doing this as it is easy to make too many files become readable & writeable for users that may have compromised security themselves

---

