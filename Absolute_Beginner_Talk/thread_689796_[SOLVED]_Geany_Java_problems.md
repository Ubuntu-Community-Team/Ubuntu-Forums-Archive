---
title: "[SOLVED] Geany Java problems"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by libertas on 2008-02-06
I use JRE Creator at school for all of my java creating. I decided that it would be great if i could take some of the work home so that i don't have to rush all of the time... i tried using eclipse and it didn't like some of the programs (Keyin) so i looked for an alternative... GEANY

now it compiled my java works and keyin as well (keyin is a java applet that the user to input data for  variables and the like) but as i tried to execute it it wouldn't allow me to. so here is the problem everything compiles fine but it would execute, it comes up with this error at the bottom of the screen

"failed to execute [file name].java (make sure it is already built)" this feels like i am making a simple mistake but i don't know what to do... PLEASE HELP!

---

### Post by jordanmthomas on 2008-02-06
Hm, have you tried just running it manually?
cd to the directory with your classes and compile / run it yourself.  Does this work?

---

### Post by emarkd on 2008-02-06
Well, *.java files are uncompiled source code. *.class files are compiled java bytecode.  Are you sure you're trying to execute the proper file?

If so, what happens if you first compile your *.java files using javac?

---

### Post by jordanmthomas on 2008-02-06
Also, make sure that when you go "Execute" in geany, that the file you want to run is open.

Like, if you have a main driver for your program called Driver and some other class called ClassB, make sure the editor is editing the file Driver.java when you compile / execute.

I just tried an old project of mine in Geany and it worked when I did it this way.

---

### Post by libertas on 2008-02-06
i just tried opening the file by going Open>Caswell Catering.java and it compiled but would not execute. i do not understand what you mean by driver and the like could you please tell my how to make it work from where i am now... im sorry that i have to drag this out and i apologize for the inconvenience it has caused.

---

### Post by emarkd on 2008-02-06
Do you get an error?  I don't know what Geany is, but if you've got a compiled java bytecode class, can you run it from the command line with

```
java /path/to/whatever.class
```

---

### Post by jordanmthomas on 2008-02-06
> **libertas said:**
> i just tried opening the file by going Open>Caswell Catering.java and it compiled but would not execute. i do not understand what you mean by driver and the like could you please tell my how to make it work from where i am now... im sorry that i have to drag this out and i apologize for the inconvenience it has caused.

Don't worry about any inconveniences.  If people thought it was an inconvenience to help, they wouldn't do it.  :)
All I meant by Driver class, etc. is if you have more than one file in a project (for example something like this)
```
Block.java           GameSave.java        Menu.java           Screen.java
Character.java       GameWin.java         Player.java         Section.java
Configure_Menu.java  Inventory_Menu.java  PlayerDeath.java    SectionGUI.java
Enemy.java           Level.java           Projectile.java     Trap.java
Game.java            Load_Menu.java       RandomNumbers.java  Weapon.java
GameOver.java        Main_Menu.java       Save_Menu.java

```
Now, when I go to run my project I run the Screen class (just an example here) because it has my **main** method.  If I had all these files open in geany I would need to be editing Screen.java when I went to execute or it would try to execute whatever I am editing.  Since I can't really run my GameSave.java, it would not work.  See what I was trying to say now?

> java /path/to/whatever.class
It's worth noting that you SHOULD NOT put the .class at the end and also that if whatever.class has classes it depends on in the same directory, you'd need to do this:
```
java -cp /path/to /path/to/whatever
```

---

### Post by emarkd on 2008-02-06
> **jordanmthomas said:**
> It's worth noting that you SHOULD NOT put the .class at the end and also that if whatever.class has classes it depends on in the same directory, you'd need to do this:
```
java -cp /path/to /path/to/whatever
```

:)  You're right, of course.  Shows how long it's been since I coded java. Thanks for the correction.

---

### Post by libertas on 2008-02-06
when i did that i got this Exception in thread "main" java.lang.NoClassDefFoundError: /home/eric/Desktop/Stuff/Projects

This is the first time that i am using Geany and what i want to do is open a whole new ... everything, project, class, .java  

can anyone tell me how to get to the point where i would have everything ready so that i can enter my information? and it press compile, execute and have it popup?

also if this is too tedious can anyone tell me where i can find some good tutorials on how to use geany?

---

### Post by jordanmthomas on 2008-02-06
Let me make sure I'm right in what I am thinking you did here:
You typed
```
java /home/eric/Desktop/Stuff/Projects
```
*without* typing the name of the class you wanted to run?

I just installed geany after reading your post and it "just worked" for me.

So, what I am thinking is wrong perhaps is that it has something to do with this Keyin thing you're talking about.  Let's see if geany works right at all.
1.  Open up geany
2.  Make a new file and paste this in.
```
public class Test
{
	public static void main(String[] args)
	{
		System.out.println("Testing Geany.");
	}
}
```
Save it somewhere as Test.java
Then see if you can compile / run it.

If it works, chances are your CLASSPATH variable is not set up right and it can't find your classes when you're trying to use Keyin. 
If it comes down to it, there's also other IDEs for Linux (TONS of them).  Code::Blocks is another popular one people like.

---

### Post by libertas on 2008-02-06
the files that i am trying to run do not have any .class files with them or projects attached they are just the  .java files

this one is called 
caswellcatering.java

when i got to make it work i can compile it... it works fine but when it comes to executing it it says that i should "(make sure it is already built)"

i hope this helps you... help me:)

---

### Post by jordanmthomas on 2008-02-06
You say it has compiled, but if you don't have any .class files, it has not compiled.
When you go to build, does it say **"Compilation Finished Successfully."** down in the compiler window?

P.S.  Sorry my fonts look bad.  I need to recompile libxft but haven't got around to it yet.


edit:  my screenshot was messed up, fixed it

---

### Post by jordanmthomas on 2008-02-06
Try this, too:
```
cd ~/Desktop/Stuff/Projects
javac caswellcatering.java
java caswellcatering

```
What happens here, does it compile and run?

---

### Post by libertas on 2008-02-06
your thing worked... perfectly finally SOMETHING worked... thankyou very much for that i needed something that worked... even if it was a test... what i am trying to do is run a .java (CaswellCatering) that requires another .java (keyin) to work. Caswell uses Keyin to allow the user to input stuff, answer questions and the like (Ex. if i add a variable called "answer" and i say

answer= Keyin.inString ("what is your name? ");

then the person who opens it will be confronted with this question and will type in thier name (Ex. John) now the variable "answer" contains the name John in it and i can use that in other sentances like

System.out.println ("Hello "+answer);

and it will print out

Hello John

this is what keyin does.

i think that my problem is with the using of the two files together maybe? ill try a few more different things... and i thankyou you have been much help to me... i was getting rather frustrated...
:)

---

### Post by jordanmthomas on 2008-02-06
Heh, I had a class like that when I was first using java too.  Mine was called Keyboard and it makes getting input a LOT easier when you don't know much about java.

Your problem may be your CLASSPATH variable.

In a terminal, what does 
```
echo $CLASSPATH

```
give you?

You'll likely want to have "." (your current directory) in your CLASSPATH so that java and javac can find all the classes (compiled .java files) you need.

To do this, just type this:
```
echo "export CLASSPATH=$CLASSPATH:." >> ~/.bashrc
```
After you log out and back in, java may be a little happier.

Also, did what I suggest running above work?

---

### Post by libertas on 2008-02-06
i tried what you said and it didn't like me lol but i did try my own little test thing... the same as you just over again and it work... so i tried inputting instead of the 

System.out.println ("test");

i put in all of my information... it worked!!!! i don't know what i was doing wrong but what ever you told me to do did... i just hope that i can duplicate it!!!! thank you very much im sure that ive found what the problem is

you have helped me alot on this ...:) thankyou very much!!!!!!!!!!!!!!

---

### Post by jordanmthomas on 2008-02-06
Well, it disturbs me to not know exactly what was wrong.  Maybe the file was saved in the wrong place before? 

Still, glad you got it working.
:popcorn:

---

### Post by libertas on 2008-02-06
i found what it was the class name "class caswellcatering" was different from what i saved it as ... caswell.java because i had to resave it and i guess i didn't use the right name... thankyou i feel so relieved now!!!

---

