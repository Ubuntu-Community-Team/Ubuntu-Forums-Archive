---
title: "Can somebody explain the &quot;System\Preferences\Keyboard Shortcuts&quot;?"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-05
Hi All!
I went to "System\Preferences\Keyboard Shortcuts", & found for example:

To lauch the "Calculator", type:         0xa1

Can somebody explain how does this work?

I typed: "zero", "x", "a", and "1", but the Calculator program did not lauch.

What am I doing wrong?

And by the way, why does the shortcut have to be so complex?

How about: " Alt+Shift+C" for calculator?

Isn't the later easier to comprehend?

Waiting for your response....
Thanks.

---

### Post by bartbes on 2006-02-05
0xa1 is  or binary or hexademical, but you can assign a new keyboard shortcut by just clicking and then typing a new one

---

### Post by dvarsam on 2006-02-05
So, how do I type the shortcut "0xa1", to lauch the "Calculator"?

---

### Post by bartbes on 2006-02-05
well, actually, I don't know, but what you can do is what I said: [quote=bartbes]you can assign a new keyboard shortcut by just clicking and then typing a new one[/quote] in your case hold ALT and SHIFT and press C and you will see <alt> <shift> c ( or something like it)

---

### Post by dvarsam on 2006-02-05
I understand that I can change the shortcut.

However, the question that arises, from all these type of shortcuts listed there, is:

Why would the programmers who created Ubuntu, BY DEFAULT, put a "0xa1" shortcut & how can this be entered by the keyboard, to launch the "Calculator" program...

Otherwise, the programmers SHOULD have used a more NORMAL command, like the one you said!

Can somebody answer to that?

---

### Post by bartbes on 2006-02-05
just the programmers, so I don't think you have luck asking it here, maybe f you have luck a programmer watches this thread and answers it, but I don't think so

---

### Post by jamesgthag on 2007-10-27
The 0xa1 is a hexadecimal number that your keyboard sends when a button is pressed.  Every key pressed sends a certain hexadecimal code to the computer telling it which was pressed  (including the numbers and letters) .  

I own a Memorex MX2500 multimedia keyboard and it has a special button with a calculator picture on it.  Pressing this button makes the calculator app pop up.  Most multimedia keyboards with a calculator button sends the 0xa1 code.  That's probably why the programmers used it as the default.  If your keyboard doesn't have the calc button, you can try binding it to some other button combination.  Good luck.

James

---

### Post by stomponthis on 2007-10-27
Yeah I have a M$ keyboard (I won it!) and I have those hexidecimal numbers in my keyboard shortcuts too.
For my browser to launch, you press the browser key, which is XF86WWW.
The one for the calculator is default isn't it?

---

### Post by scorp123 on 2007-10-27
> **dvarsam said:**
>  However, the question that arises, from all these type of shortcuts listed there, is: Why would the programmers who created Ubuntu, BY DEFAULT, put a "0xa1" shortcut & how can this be entered by the keyboard, to launch the "Calculator" program... Some people have "Multimedia Keys" on their laptops or additional buttons on their keyboards which will precisely produce the required key-code. :)

And if it does not it is easy to change it :)

---

### Post by jamesgthag on 2007-10-27
Does anyone know how to manually enter the hexadecimal numbers?  And do you know of a easy program to capture the key presses and show you the hexadecimal codes for a key pressed?  

I tried re-assigning my stupid DOS key to the run a terminal command using: 

System --> Preferences --> Keyboard Shortcuts

and nothing happens.  Other buttons on the keyboard work such as CALC, PLAY, STOP, REW, FWD, WWW, EMAIL, MUTE, etc.  The non-active ones include: PHONE, MYDoc, DOS, NEWS, SLEEP, WAKE, POWER, COPY, CLOSE.

---

### Post by scorp123 on 2007-11-01
> **jamesgthag said:**
> Does anyone know how to manually enter the hexadecimal numbers?  And do you know of a easy program to capture the key presses and show you the hexadecimal codes for a key pressed?   Our friends in the Gentoo Wiki have written a nice "How to" on this:
[http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys)

When they mention "emerge xyz" you'd instead do "apt-get install xyz" on Ubuntu; 'emerge ...' is the Gentoo command they use to download and install programs (that's a simplified explanation ... I know) so for us that would be 'apt-get install ...'

---

### Post by drs305 on 2007-11-01
> **jamesgthag said:**
> And do you know of a easy program to capture the key presses and show you the hexadecimal codes for a key pressed? 


I'm not at my linux machine at the moment, but IIRC type this in terminal:
```
xev
```

It will open a small window and when you hit a key it will reveal the code.

---

