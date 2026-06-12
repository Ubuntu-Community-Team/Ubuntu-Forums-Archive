---
title: "Program installing and uninstalling"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by ekdysiast on 2007-03-12
My problem started with emacs but I'm more curious about the general methodology of installing and uninstalling in Linux, so I'm posting my question here.

I downloaded and compiled emacs from a CVS repository and, of course, to top it all off, I did 
```
sudo make install
```

When I executed emacs, the icons were kind of off, not as flashy (which is a relative term here) as the emacs I'm familiar with. Not knowing that make could also do uninstall, I just went to "/usr/local/bin/" and deleted the entire "bin" directory where emacs and only emacs was installed.  Then I did it the recommended way, which is
```
sudo apt-get install emacs
```

When I typed emacs in the command line, the OS would only search in /usr/local/ rather than wherever it was that emacs had installed itself and tell me that it couldn't find emacs in that path. So I did
```
sudo apt-get uninstall emacs
```

Then, looking around, I discovered make also does uninstall, so I went to my emacs source code directory and did
```
sudo make uninstall
```

which threw me an error message, obviously, since I had just demolished /usr/local/bin in one gesture.

Now, my guess is, just as there is a registry in Windows which handles program install paths, there is also one in Linux. 

Would anyone mind telling where that is so I can just manipulate it myself?

---

### Post by raja on 2007-03-12
The easiest route is to let your package manager handle all this. So if the program available in the repository is enough for you, install it with apt-get or aptitude. If you do want to compile from source, check install is a better last step than make install. That way the installation is done with the package manager and it is easy to uninstall later.

---

### Post by ekdysiast on 2007-03-12
Thanks, that's what I'm planning to do from now on. But since I've already fouled something up, I'd rather correct it than reinstall ubuntu. I'd like to know how to do that.

---

### Post by coffeeadikt on 2007-03-15
I was browsing for something else when I came across this thread. I'm smiling because this was my first pleasant surprise when working with Linux too.

> **ekdysiast said:**
> Now, my guess is, just as there is a registry in Windows which handles program install paths, there is also one in Linux.

Nope :)  There is no registry in Linux.

It looks to me like you completely undid your learning experience there.

---

