---
title: "reverse engineer .exe files?"
date: 2011-09-02
forum: Any Other OS
---

### Post by match417 on 2011-09-02
how do I reverse engineer .exe files? I have an exe program that upgrades the firmware on this device I have, and I want to be able to see if it pulls a file from the software on my computer after being triggered or if the exe program pushes the firmware upgrade to the device when told to. That way I can write a program for my android phone for pushing the firmware upgrade to the device. So I don't always have to start up windows instead of linux to upgrade it, I can just do it from my android phone.

Is there a program I can use to rip apart the exe? Is there a linux program that I can use for this?

Thanks!

---

### Post by ClientAlive on 2011-09-02
[http://www.google.com/search?client=opera&rls=en&q=what+is+a+decompiler&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=what+is+a+decompiler&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)


[http://www.backerstreet.com/rec/rec.htm](http://www.backerstreet.com/rec/rec.htm)

---

### Post by Habitual on 2011-09-02
It's a push, else you wouldn't need the .exe (if the software was already on the system, what's the need for an(other) exe?

---

### Post by Habitual on 2011-09-02
you could 'peek' into the exe using ```
strings /path/to/exe
```

but that only shows the Windows API stuff. but it could help if you know how to decode that noise. :)

---

### Post by match417 on 2011-09-02
I have the program decompiled in rec4, but it keeps shutting down due to errors so I have to keep saving the project.

What type of command would I be looking for to find where it transfers over a db9 serial connection?

---

### Post by ClientAlive on 2011-09-03
> **match417 said:**
> I have the program decompiled in rec4, but it keeps shutting down due to errors so I have to keep saving the project.

What type of command would I be looking for to find where it transfers over a db9 serial connection?


Never used a decompiler before (or a compiler for that matter). I'm just getting into all this and kinda learning as I go. Sorry I can't be of more help.

---

### Post by Sef on 2011-09-03
Moved to Other OS Talk.

---

### Post by alegomaster on 2011-09-04
You could contact the publisher of the .exe file and ask him/her about the question instead of going through all of this reverse engineering. 

Actually we should try to reverse engineer files so we can finally make Windows open-source.:)

---

### Post by cgroza on 2011-09-04
> **alegomaster said:**
> 
Actually we should try to reverse engineer files so we can finally make Windows open-source.:)
That is still illegal.

---

### Post by match417 on 2011-09-04
> **alegomaster said:**
> You could contact the publisher of the .exe file and ask him/her about the question instead of going through all of this reverse engineering. 

Actually we should try to reverse engineer files so we can finally make Windows open-source.:)

I've already contacted them and I haven't heard anything.

LOL..yeah..windows needs to be open source so that people can actually fix the microsoft guys spagetti-patch programming so that less memory is used.

---

### Post by ClientAlive on 2011-09-05
> **cgroza said:**
> That is still illegal.

Maybe but it certainly isn't unethical.

:guitar:

---

### Post by ClientAlive on 2011-09-05
> **match417 said:**
> I've already contacted them and I haven't heard anything.

LOL..yeah..windows needs to be open source so that people can actually fix the microsoft guys spagetti-patch programming so that less memory is used.

I programming is like a recipe then is windoZ like a bowl of puke?

I'm kidding, sort of . . .

:P

---

### Post by match417 on 2011-09-05
lol, the unethical thing would be charging people $300 every two years for an operating system and $200 for a new office suite every two years, while convincing them that what they have isn't good enough. On top of that making a new file extension called docx so when your workplace switches to it you have to purchase the new copy to be able to read it on your laptop. Besides, I'm a car guy, I'm not going to spend money on software when I could buy a new turbo. :)

---

### Post by KiraLexi on 2011-09-09
How is that unethical? Nobody is forced to buy a new operating system. It's their choice.

I also fail to see how illegally disassembling someone else's commercial product would possibly be ethical, or even a remotely good idea.

---

### Post by match417 on 2011-09-09
the commercial product in question that I am looking into disassembling is not sold, it comes free with purchased equipment and is actually free for anyone to download and install. It can't be unethical to disassemble something that's free. I do agree with you that it would be unethical to disassemble something that can be purchased, so that someone could make something that's a free alternative. I just want to take a free program for a laptop, and run a stripped down version of it on my phone.

---

### Post by qamelian on 2011-09-09
> **match417 said:**
> It can't be unethical to disassemble something that's free. 
Just because the software is provided without charging a fee for it does not make it ethical or legal to decompile or reverse engineer it. There are plenty of programs out there provided at no charge that explicitly prohibit doing this in the included license.

---

### Post by match417 on 2011-09-09
I'm not worried about it, there is no license agreement, you don't actually install the program, there is no "do you accept the terms..." or anything like that. When you run the exe, the program starts. If they didn't want me to do this they would have a license agreement written out that I have to agree to. Other situations would be unethical, this is not. If i'm developing something to sell it, that's one thing, this is just for me to use.

can we end this unethical/ethical discussion?

---

### Post by KiraLexi on 2011-09-10
Just to be clear, I wasn't saying that reverse-engineering whatever driver or similar tool you're talking about is unethical. I was referring to the guys talking about RE'ing Windows, which is probably unwise.

My personal favorite tool (if you're comfortable with assembly language) is IDA Pro.

---

### Post by qamelian on 2011-09-10
> **match417 said:**
> I'm not worried about it, there is no license agreement, you don't actually install the program, there is no "do you accept the terms..." or anything like that. When you run the exe, the program starts. If they didn't want me to do this they would have a license agreement written out that I have to agree to. Other situations would be unethical, this is not. If i'm developing something to sell it, that's one thing, this is just for me to use.

can we end this unethical/ethical discussion?
Unless you have been given explicit permission by the developer, what you want to do is illegal in many countries. If they wanted you to be able to modify the software, they would make the source code easily available. In this case, it is likely the the license is implicit because the software is paired with another product, as you mentioned earlier, or the software is also given coverage in the terms & conditions of use of the other product. Whether or not you are developing something to sell is moot, as most restrictions are expressed in terms of both commercial and personal use.

Whether or not you agree with it, that's just the way it is.

---

### Post by ClientAlive on 2011-09-11
> **KiraLexi said:**
> How is that unethical? Nobody is forced to buy a new operating system. It's their choice.

I also fail to see how illegally disassembling someone else's commercial product would possibly be ethical, or even a remotely good idea.


They're forced de facto by not having support for anything but Windoze and then running into situations (be it work or school or something else) where they are required to use some program that only runs on the Windows platform - kinda like I just had to deal with. As a part of my online college courses I was required to install something called "LockdownBrowser" to take quizes through. You can not take the quiz without doing it in this browser. This browser is available for Mac and Windoze - that's it. I was FORCED to install windoze on a machine I spent two months of my time, money, and effort, resurrecting for an entirely different purpose. Not only was I forced to install windoze (something I have no desire to do on my own) but my machine, my hardware itself, that I spent my money on, was jacked in the process. People run into this situation constantly. Not just me and not just occasionally. People are forced. You better believe it.

---

### Post by KiraLexi on 2011-09-11
> **ClientAlive said:**
> They're forced de facto by not having support for anything but Windoze and then running into situations (be it work or school or something else) where they are required to use some program that only runs on the Windows platform - kinda like I just had to deal with. As a part of my online college courses I was required to install something called "LockdownBrowser" to take quizes through. You can not take the quiz without doing it in this browser. This browser is available for Mac and Windoze - that's it. I was FORCED to install windoze on a machine I spent two months of my time, money, and effort, resurrecting for an entirely different purpose. Not only was I forced to install windoze (something I have no desire to do on my own) but my machine, my hardware itself, that I spent my money on, was jacked in the process. People run into this situation constantly. Not just me and not just occasionally. People are forced. You better believe it.

You sound like a fanatic.

---

### Post by ClientAlive on 2011-09-13
> **KiraLexi said:**
> You sound like a fanatic.


If what you're referring to is fanatical about a person's freedom to choose then I'll take that as a compliment.

I'm just a person who doesn't think it's fair to use money and power to take advantage of others. When a person has a desire to use other products (and there's multiplied thousands of us), and the cost to companies to make that possible is so very minimal, I think the right thing to do is make it available. So many companies fail to do so (for whatever reasons) that the freedom to choose is virtually eliminated. It isn't just an outright travesty of justice, it's rude, and offensive.

---

