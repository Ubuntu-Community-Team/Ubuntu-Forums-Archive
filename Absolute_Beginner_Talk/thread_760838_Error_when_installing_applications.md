---
title: "Error when installing applications"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by roocraig on 2008-04-20
I incorrecly downloaded a mac os 10.4 ppd file for the ablility to print to my wireless laser printer. I tried to install it an got an error. I figured out how to install the printer finally, but now when I download applications I get an error that the printer driver was not installed. How do I clear that when I install additional programs-kind of annoying though. Thanks in advance.

Ryan:(

---

### Post by sdennie on 2008-04-20
You might be able to fix it using:

```

sudo apt-get install -f

```

---

### Post by roocraig on 2008-04-20
what does this command do? I have no clue. Here is the error code:

E: cupswrappermfc7820n: subprocess post-installation script returned error exit status 1

When I went to install the drivers for the printer it said that I could use a ppd file. I went to the brother website and got the Mac OS X 10.4 version file because I thought that since Mac is Unix that it would be compatible. When I clicked on the file to try to install it it gave me an error and now I get an error everytime I go to install another program. The error happens after the programs have been successfully installed. I have no clue where to go to rectify the situation. Thanks for reading.

Ryan

---

### Post by paydaydaddy on 2008-04-20
> **vor said:**
> You might be able to fix it using:

```

sudo apt-get install -f

```

This command attempts to resolve or fix broken packages. It may not fix your problem, but it won't hurt anything to try it.

---

### Post by roocraig on 2008-04-20
How will I know if I solved the error problem? Is there anyway to get rid of the error? It was only a double click not an installation

Ryan

---

