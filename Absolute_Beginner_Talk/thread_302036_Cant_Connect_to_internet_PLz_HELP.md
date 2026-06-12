---
title: "Cant Connect to internet PLz HELP"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2006-11-18
I cant connect to internet anymore with firefox just after upgrading the ubuntu6.06
i can connect with the other computer.
I need help plz

---

### Post by robinl on 2006-11-18
Well no-one can help you with so little information; what did you do between your last successful internet connection and now? Did you try another browser? Can you go on your LAN? Do you have a valid IP? etc etc etc. 

So give us all the information you have when you ask a question for someone to help you.

---

### Post by kiyometane on 2006-11-18
I was getting connection before firefox was upgraded with the system upgrade.
I still have lan connection
Is there a default browser i can connect to internet?
Is there a way to set firefox to default?

---

### Post by BaffledMollusc on 2006-11-18
> **kiyometane said:**
> I cant connect to internet anymore with firefox just after upgrading the ubuntu6.06
i can connect with the other computer.
I need help plz

When you say "after upgrading the ubuntu 6.06" do you mean that you upgraded from 6.06 to 6.10? Or do you mean you used the software update function to upgrade some package (e.g. some security update) but stayed with 6.06?

Also, what happens if you open a terminal window and type "ifconfig"?

(You can find the terminal under "System->Konsole Terminal Program" if you're using Kubuntu; I'm not sure where it is if you're using Ubuntu.)

The more information you can give us, the better the chance of us fixing the problem.

---

### Post by kiyometane on 2006-11-18
I did the software update. It tried to install the firefox 1.5.0.7
when i type "ipconfig" it says command not found

---

### Post by BaffledMollusc on 2006-11-18
> **kiyometane said:**
> I did the software update. It tried to install the firefox 1.5.0.7
when i type "ipconfig" it says command not found

The command is "ifconfig" not "ipconfig" (bizarre, I know). Try that and see what happens.

Also, you say you have a LAN connection. What happens if you open a terminal window and type "ping www.google.com"? Is it reachable?

Can you start any web browser at all, or did the update screw up the package so badly that you can't even start Firefox?

Finally, are you using Ubuntu or Kubuntu?

---

### Post by kiyometane on 2006-11-18
I'm using ubuntu6.06
I can start firefox but it would not connect to the internet.
when i type an address it can be displayed. Only the home page could accessed.
Ifconfig command shows a text file, but i dont know what it reads

---

### Post by BaffledMollusc on 2006-11-18
> **kiyometane said:**
> I'm using ubuntu6.06
I can start firefox but it would not connect to the internet.
when i type an address it can be displayed. Only the home page could accessed.
Ifconfig command shows a text file, but i dont know what it reads
Okay.

I need to know if your computer can reach the outside word. In a terminal window, type "ping www.google.com"

This will try to contact Google with test data over and over. If this succeeds, then we know that your network is fine and there's something wrong with Firefox. After you type "ping www.google.com" and press "enter", you should see information appear, one line at a time, with a couple of seconds between each new line.

Wait about ten seconds, then press "CTRL C" to stop it. Now copy and paste what the terminal says into a message here. The easiest way to copy and paste from a terminal is to select the text with the mouse, then left-click somewhere in the new message you're typing, and then press the middle mouse button.

It would also help if I knew what the output of "ifconfig" was. Could you  copy and paste the text from "ifconfig" so I can see what it is?

Thanks!

---

### Post by kiyometane on 2006-11-18
when i type "ping www.google.com"
i get " unknown host [www.google.com](www.google.com) "
There is no way i could post you the file since the computer cannot 
connect, unless there is a linux default browser.

---

### Post by kiyometane on 2006-11-18
I think it would be easier i do a fresh install of the operating system and hopefully with a success on intalling.
I'll then tell you exactly what i did so that i dont make the same mystake again

---

### Post by robinl on 2006-11-18
A fresh install shouldn't be neccessary. Please post the output of this command from the terminal:

```
ifconfig | grep inet
```

---

### Post by BaffledMollusc on 2006-11-18
> **kiyometane said:**
> when i type "ping www.google.com"
i get " unknown host [www.google.com](www.google.com) "
There is no way i could post you the file since the computer cannot 
connect, unless there is a linux default browser.
Oh, of course! Sorry, I wasn't thinking.

Okay, I'm really not an network expert, so I'm not sure how much help I can be here. Hopefully someone else can help you.

The "unknown host" error shows that the problem you're having isn't related to Firefox. It means that your computer can't access the internet. It does seem strange that this happened just from updating Firefox, though. 

Let me absolutely sure I understand what happened: You were using Ubuntu 6.06, and you could use the internet without problem. You then got the icon that meant that there were updates available. You clicked on it and installed the updates. One of the updates was Firefox 1.5.0.7. The updates all installed correctly and there was no error message. Right after the updates you could not access the internet. Is all this correct?

I have had a similar problem, but that was because the updates also included a kernel update. This broke the drivers I was using for my wireless card. If you're not using wireless internet then this probably isn't the problem.

A few more questions:

Did you initially have any trouble getting the internet to work with Ubuntu? Did you have to install any special drivers or software like nsdiswrapper?

Do you know what else was updated when you updated Firefox?

---

### Post by kiyometane on 2006-11-18
I just made a fresh install of ubuntu 6.10. But i still cant connect to internet.
I dont know how i would solve it

---

### Post by AAM on 2006-11-18
Dear **kiyometane**,

you seem to be in a panic, please follow the instructions of **BaffledMollusc** and others. To work out the problem, you need to provide the information that they are asking for.

Are you using a wireless connection or ethernet cable connection to your broadband router?

Also go back over the previous helper's instructions and give them what they ask for. We are blind to what is happening on your system without this information.

AAM

---

