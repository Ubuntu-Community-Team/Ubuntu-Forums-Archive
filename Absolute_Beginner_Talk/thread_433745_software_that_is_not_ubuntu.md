---
title: "software that is not ubuntu"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-05-05
I'd like to try the open source multimedia authoring tool celtx ([www.celtx.com](www.celtx.com)) which isn't in the repository;but the warnings I've seen posted about trying to upload sw that isn't in the repository frighten me. I'm worried I'll spend a lot of time and in the end only break something.  So- 2 questions, if I may:

a) how does sw get in the repository? Is this program likely to be going there soon? Can I nominate it for the repository somehow?

b) if it's not in the repository, and isn't going there,   can a complete newbie like me break things by trying to load it in my ubuntu? Is there an idiot's guide about exactly what to do?

Thanks


ginestre

---

### Post by Roadrunner777 on 2007-05-05
There is some great information on installing at this [website]("http://www.cutlersoftware.com/ubuntuinstall/").  It answers your questions and probably the ones you havn't thought of yet.  I'd answer directly, but I'd just be copy and pasting from their website.  Check it out.

---

### Post by Rotaj on 2007-05-05
Did you try only Aptitude (Add/Remove), or did you search thought Synaptic - System/Admimstration?

You have done some research to find Celtx in the first place. And since Ubuntu is based upon Debian, there may be a debian versian to install. You may have to do a little more research to get the right answers.

---

### Post by ginestre on 2007-05-05
Thanks for the replies.  I looked in synaptic, an d didn't find any reference to the program celtx; but on the celtx.com website there is a debian version to be downloaded as well as a forum on which some other people have asked about ububtu installations. It looks from the forum as though about half of the time there are problems, and as a newbie that sounds like difficult odds to me... particularly after reading all the warnings about not using non ubuntu software

---

### Post by tageiru on 2007-05-05
It is trivially easy to get it to run. Unpack the file and run the celtx binary. You don't need to install it.

---

### Post by ginestre on 2007-05-05
> **Roadrunner777 said:**
> There is some great information on installing at this [website]("http://www.cutlersoftware.com/ubuntuinstall/").  It answers your questions and probably the ones you havn't thought of yet.  I'd answer directly, but I'd just be copy and pasting from their website.  Check it out.

Thanks. That is one very clear site!

---

### Post by ginestre on 2007-05-05
> **tageiru said:**
> It is trivially easy to get it to run. Unpack the file and run the celtx binary. You don't need to install it.

Thanks for the pointer, but I obviously don't understand something. I downloaded the tar, unpacked it into a new directory I called progs, went there and clicked on a file called celtx-bin, marked as executable. Nothing happened. What did I do wrong?

---

### Post by 3rdalbum on 2007-05-05
Right-click on the celtx-bin program and choose Properties. Under the "Permissions" tab, check to see that your user has permission to execute the program.

It will probably be beneficial to run the program inside a terminal, so you can check if it is giving any error messages. To do this, install the "nautilus-open-terminal" package from Synaptic. After it is installed, right-click in the directory that contains celtx-bin, and choose "Open in terminal".

In the terminal that opens, type:

```
./celtx-bin
```

---

### Post by ginestre on 2007-05-05
Thanks to all for the answers. It really was simple and less frightening than I feared.

For posterity-the solution, should there be anyone else as clueless as me who wants to do this:

download the package from [www.celtx.com](www.celtx.com) and unpack it somewhere convenient on your hd
go there
find the file celt-x shell script
click on this to launch
in the dialogue box, reply YES to the question 'Run in terminal?'

Again, thanks to all. It's all very encouraging. (and in 5 weeks of using ubuntu, the PC hasn't crashed once. Not like some other o/s I could mention....)

---

### Post by fedorovsky on 2007-05-08
-

---

