---
title: "cannot add medibuntu source"
date: 2012-05-25
forum: Any Other OS
---

### Post by HappyLinux on 2012-05-25
I've just installed Mint 13, and everything in getting things up and running has been mainly smooth. Minimal hassle you could say.

However, one repository refuses to be added to the source list. Medibuntu.

I've gone to the Medibuntu website and followed the info there.

I in-putted this into the terminal

> sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

however, this is the results.

> --2012-05-25 15:14:20--  [http://www.medibuntu.org/sources.list.d/maya.list](http://www.medibuntu.org/sources.list.d/maya.list)
Resolving [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org](www.medibuntu.org))... 88.191.127.22
Connecting to [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org)|88.191.127.22|:80](www.medibuntu.org)|88.191.127.22|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-05-25 15:14:20 ERROR 404: Not Found.

Is anyone else having the same problem, or am I missing something?

---

### Post by kc1di on 2012-05-25
since your install it on Mint 13 you should ask your question in the mint forums.  

Though mint and Ubuntu share a common base there are differences.

however this ppa may work for you too. but don't tell the mint crew I told you to us a PPA. :)
[http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/]("http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/")

the other reason it may not be there is because in mint all the codecs are already installed and you don't need them.

---

### Post by HappyLinux on 2012-05-25
I previously considered going to the Mint forums, but chose to stay here because yes, Mint is based off Ubuntu. So far, I haven't had any complaints about posting requests for help with Mint here.

I previously went to that very site as well, in my quest to find help with this. The same error message came up.

However, I just took a look at my sources list, and to my surprise, medibuntu has been added. Strange that it comes up with an error message but does the job anyway.

---

### Post by Curtis6767 on 2012-05-25
Unless your copy/paste had an error, then you should be okay.

did you?

```
sudo apt-get update
```after you ran your first command?

And did you follow the steps here: [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

And does you software sources look like the image?

---

### Post by HappyLinux on 2012-05-26
Yep, I ran that update command. Also, you'll see in the screen shot, the source thingy is on my list, even after the error message.

---

### Post by Curtis6767 on 2012-05-26
You might try looking over the site below, which has step-by-step instructions on how to manually install the Medibuntu repos. It's for Ubuntu but shouldn't be too different from Mint/Maya.

[http://www.liberiangeek.net/2011/04/add-medibuntu-repository-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/04/add-medibuntu-repository-ubuntu-11-04-natty-narwhal/)

I think before you do the above steps, that you would first want to delete the Medibuntu that you already have in your sources list and start over from there.

Hope this helps.

---

### Post by HappyLinux on 2012-05-27
That link goes to a page for Ubuntu 11.04. However, I have done as you suggested and removed the Medibuntu from my sources list before following the instructions on the site. So far, no problems.

However, I can't find Medibuntu in my software manager. However, seeing as I have it in my sources list, it can stay there. Better to have and not need... you get the idea.

Cheers.

---

### Post by Curtis6767 on 2012-05-27
If you cchanged this:

```
deb http://packages.medibuntu.org/ **natty** free non-free
```To this:

```
deb http://packages.medibuntu.org/ precise free non-free
```Then that's probably about the best you can expect for now. 

I just use the Ubuntu software center and Medibuntu does not show up anywhere in there, but I do have it in my software sources list. 

I think at this point you might want to haunt the Mint/Maya forums and see if others are having this same issue and if so then someone there might come up with a real solution.

GL

---

### Post by HappyLinux on 2012-05-28
I am already considering creating an account in the Mint forums.

I already took the initiative and changed natty to precise on that line.

---

