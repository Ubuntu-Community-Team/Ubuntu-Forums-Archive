---
title: "Any WinSCP equivalents for Ubuntu?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by spcoex on 2007-11-02
Hi everyone, 

Im a big fan of using WinSCP on my desktop (windows).....is there a WinSCP equivalent for Ubuntu desktop....I cant seem locate anything.

---

### Post by KCPokes on 2007-11-02
gFTP will allow you to use FTP and SSH, much like WinSCP does.  For the most part it can be used in place of WinSCP.

---

### Post by rajan on 2007-11-02
you can also use simply scp from the command line. because it doesn't have the GUI, you can do a lot more flexible things with it, but you'll have to be comfortable with the command line.

---

### Post by bingoUV on 2007-11-02
> **spcoex said:**
> Hi everyone, 

Im a big fan of using WinSCP on my desktop (windows).....is there a WinSCP equivalent for Ubuntu desktop....I cant seem locate anything.

I too am a fan of WinSCP on windows. I open only text files using WinSCP, and I anyway use vim editor to edit them on windows too. So vim's remote file editing feature is a kind of replacement for me. I am briefly describing it, in case you were not aware.

```

:e scp://<username>@<hostname>//full/path/to/file/to/edit
:e scp://<username>@<hostname>//full/path/to/directory/to/browse/

```

You can create shortcuts for your favourite folders, like in .vimrc
```

abbreviate rh e scp://<username>@<hostname>//home/<username>/

```

Now :rh opens the home directory of <username> on the machine <hostname>. 

It also helps to setup public key authentication (like it does in WinSCP too).

---

