---
title: "Feisty &amp; java 6"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2007-04-24
I have just installed Feisty .. so far so good.
I was looking at installing java 6 using the instructions here ...[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

But, all of the url's use edgy..not feisty. Is it ok to use the url's and just change edgy to feitsy on th urls? 

Or is there another tutorial on how to install java 6 that I am unaware of?

Thanks for the help...!

---

### Post by DougieFresh4U on 2007-04-24
Is java 6 not in Synaptic Package Manager?

---

### Post by cjnkns on 2007-04-24
I only see 1.4 - it says we need the new repo's for java6
Unless of course I am totally missing it; which might be possible but I don't see it right now.

---

### Post by crimesaucer on 2007-04-24
you have the correct wiki, I don't understand the question.

can't you just add those repositories and then use the terminal code from this part in the wiki: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox)

---

### Post by Sef on 2007-04-24
Easy way to install Java:

Applications > Add/Remove > Which show to "All available Applications" > Search > type in Sun Java 6 > click on "Sun Java 6 Web Start&#901; > apply > apply > follow the directions to finish.

---

### Post by cjnkns on 2007-04-25
I looked in Add/Remove but didn't see java 6 in the list .. I did see 4 though; but after attempting to run this command
sudo aptitude install sun-java6-jdk sun-java6-javadb glassfish netbeans5.5

it' seems I have java6 installed now, but it also seems from my menu that I have Sun Java 6 Control Panel and the Sun Java 5 Control panel options in Preferences menu? What's with that.

When I ran th above command it didn't allow me to install glassfish or netbeans. It said I needed to move them to a directory with appropriate privilege; which is strange because I sudo 'd it...

---

### Post by Seisen on 2007-04-25
It depends on how you installed them, if you installed each one differently that would explain why you have two of them listed in the menu,

---

### Post by cjnkns on 2007-04-25
I didn't install 5... that's what I find interesting about it. all I did was issue this command...
sudo aptitude install sun-java6-jdk sun-java6-javadb glassfish netbeans5.5

Then I noticed 6 and 5 where both in the Preferences menu ..

---

### Post by crimesaucer on 2007-04-25
I'm not too sure about the java development kit, but you might want too try this terminal command to see what java you are using, and then make sure it's the one you want:

```
sudo update-alternatives --config java
```

---

### Post by jpatton on 2007-04-25
sudo aptitude

hit the forward slash /

type jre

use the arrow keys to select which jre you want and the hit the plus key

tap g twice

agree to the license agreement from sun.

all done.

when you return to the aptitude interface type q to quit.

if you want the development stuff search for jdk.

---

