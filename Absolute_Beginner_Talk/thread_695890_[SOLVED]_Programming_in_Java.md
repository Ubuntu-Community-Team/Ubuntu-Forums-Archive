---
title: "[SOLVED] Programming in Java"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by dwally89 on 2008-02-13
Hi

I want to start to program in Java (have previously programmed in VB.NET).

I've had a look through the "Add/Remove Applications" and the Synaptic Package Manager, but I'm not sure what program to install.

Thanks

---

### Post by macogw on 2008-02-13
sun-java6-jre to run programs or sun-java6-jdk to write them.

If you'd like to get the open source implementation of Java (I use it since Liferea, the feed reader I use, crashes on sites with .swf files if you use Sun, but not if you use the open source one), that'd be icedtea-java7-jre and icedea-java7-jdk  I think it's #7 because it's version 7 will be the first fully-open version of Java.

---

### Post by dwally89 on 2008-02-13
Thanks

---

### Post by piousp on 2008-02-13
You should try the NetBeans IDE, which is really good. Eclipse is another option.

---

### Post by dwally89 on 2008-02-13
Ok so I've installed icedtea-java7-jre and icedtea-java7-jdk, but I'm not sure where the actual program is located...

I now have IcedTea Java Web Start in the Internet menu, and under System>Preferences, I have IcedTea Java Plugin Control Panel and IcedTea Java Policy Tool.

Where is the program I use to actually write programs?

Thanks

---

### Post by piousp on 2008-02-13
What you downloaded is the JDK, which is the "language itself" (java's virtual machine). If your looking for an application where you can write your code, you need an IDE. Personally, I recommend the NetBeans IDE.

You can get it via apt-get, or just download the binaries from Netbeans.org

I dont know if Netbeans or Eclipse work with the icedtea java jdk tho.

---

### Post by dwally89 on 2008-02-13
Ok, so I've installed NetBeans, however when I click New Project and click on Standard, it says that it imports an **existing** Java application.

How do I create a new one?

Thanks

---

### Post by piousp on 2008-02-13
Let me make a little how-to for ya ;)
I'll post it asap

---

### Post by dwally89 on 2008-02-13
Thanks :-)

Appreciated :-)

---

### Post by piousp on 2008-02-13
First, open the Netbeans IDE.

On the menu, click on File -> Create new Project

A new window will pop-up:

Under "Categories" select "Java". Then, under "Projects", select "Java Application"

[IMG]http://img116.imageshack.us/img116/2621/newprojecthu5.png[/IMG]

Click "Next" and you'll need to Name your Project:

[IMG]http://img90.imageshack.us/img90/5809/newjavaapplicationtz5.png[/IMG]

Click on "Finish" and your good to go!

[IMG]http://img90.imageshack.us/img90/9919/helloworldprojectnetbeaxo2.png[/IMG]

I know this thing isnt a good how-to, but it will help you out (hopefully) !

---

### Post by dwally89 on 2008-02-13
Thanks so much, but when I click on New Project all I get is:
Standard
Web
Samples

Help please... :-)

---

### Post by piousp on 2008-02-13
It should be under standard -> New Java App, but it doesn't show up?
Thats weird: either you got the wrong version of netbeans, or you dont have the right JDK.
What version of netbeans did you got? If you downloaded the 6.0, get the one that says JAVA SE.
Try downloading the netbeans-java jdk bundle also.

---

### Post by dwally89 on 2008-02-13
I've got NetBeans 5.5.1

HELP!

Please :-)

---

### Post by piousp on 2008-02-13
Let me check if i have Netbeans 5.5.1

Its under general -> Java App, as you can see in the sreenshot.
[IMG]http://img218.imageshack.us/img218/9492/pantallazonewprojecthy5.png[/IMG]

If it doesn't show up, you should check which version of Java u have in your system.

---

### Post by tangibleorange on 2008-02-13
Don't wish to detract from your promotion of NetBeans :), but I find NetBeans is simply too geared towards big projects when all I write are a few simple programs. I highly reccomend the Geany IDE. Its GTK2 based and is a great little program, with code indenting, syntax highlighting, and compile/run buttons.:

> sudo apt-get install geany

Let us know what you think!

---

### Post by jaytek13 on 2008-02-13
And on that note, with everyone promoting this and that IDE, I'd recommend just using the command line. Having to learn new IDE's is really secondary to actually learning the language, and these IDE's seem to be overcomplicating things just a bit.

---

### Post by dwally89 on 2008-02-13
Got the following error when tried to install Geany

Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

EDIT: Had Synaptic Package Manager open whilst trying to install. Have installed it now. Will give it a go an report back soon

---

### Post by tangibleorange on 2008-02-13
> **jaytek13 said:**
> And on that note, with everyone promoting this and that IDE, I'd recommend just using the command line. Having to learn new IDE's is really secondary to actually learning the language, and these IDE's seem to be overcomplicating things just a bit.

No I agree with that. It's just when I first started learning Java I found the prospect of constantly having to use the command line a bit daunting. Mind you, that was before I started using Linux :guitar:

---

### Post by piousp on 2008-02-13
Sure, u can use gedit to write your programs, and then compile them with javac, but, at least for me, its more fun to use an IDE. And true, netbeans is more for big projects than just simple apps. BTW, i cant think of a good simple IDE :confused:

Sorry, i didn't meant to sound/be rude. English is not my first language and i just read what i wrote and it kinda sounds rude. :P
What i was trying to say, is that i've only wirk with netbeans and eclipse (command line and basic text editors too :P), therefor, i dont know if there are any IDE for making small apps.

---

### Post by dwally89 on 2008-02-13
Thanks for everyones help :-)

Have got Geany to work, so am using that for the mo, and am teaching my self Java.

Quick thing, I've searched the internet and can't find how to call one public static from another.

I have one called "main" and one called "main2"

How can I make main call main2?

Thanks

---

### Post by Blutack on 2008-02-13
Geany is really great, I'm not a fan of Eclipse I must say.
You don't have to use it in conjunction with the command line, it has build/run buttons in the toolbar that are keyed to the file type you open (so for example build for a .java file will run it through javac).
If you are setting out, I would not recommend a large IDE.

---

### Post by Abild on 2008-02-13
> **dwally89 said:**
> Thanks for everyones help :-)

Have got Geany to work, so am using that for the mo, and am teaching my self Java.

Quick thing, I've searched the internet and can't find how to call one public static from another.

I have one called "main" and one called "main2"

How can I make main call main2?

Thanks

```


class Main
{

public static void main(String[] args)
{
System.out.println("This is main\n Now i'm calling main2()");
Main.main2();
}
public static void main2()
{
System.out.println("This is main2");
}
}

```

---

### Post by dwally89 on 2008-02-13
Hmmm, thats what I thought, and had tried previously, but its not working.

Should I private message you my source code?

---

### Post by Abild on 2008-02-13
Why dont we keep it public in the forums others can learn from your problems?

---

### Post by dwally89 on 2008-02-13
OK
```

public class untitled {

	public static void main (String args[]) {
		System.out.println("Using a normal for loop:");
		System.out.print("Count is: ");
		
		for (int i=1; i<11; i++) {
               System.out.print(i);
               System.out.print(", ");
          }		
		
		System.out.println("");
		System.out.println("_________________________________");
		
		int[] numbers = {1,2,3,4,5,6,7,8,9,10};
		System.out.println("Using an array:");
		System.out.print("Count is: ");
          for (int item : numbers) {
            System.out.print(item);
               System.out.print(", ");
          }
        
        System.out.println("");  
        System.out.println("_________________________________");
          
untitled.main2();        
	}
	
	public static void main2 (String args[]) {
		System.out.println("Now a nested for loop =P");  
        for (int i=1; i<5; i++) {
        	for (int j=1; j<5; j++) {
        		System.out.print(i);
        		System.out.print(" ");
        		System.out.print(j);
        		System.out.print(", ");
			}
		}
		System.out.println("");
		System.out.println("_________________________________");
		
		System.out.println("Now let's try and get rid of that annoying comma at the end of lines using an if statement =)");
		
		System.out.println("But first we must check we can do if statements...");
		int k = 10;
		
		 if (k >= 10) {
          System.out.println("k = 10");
     }
     System.out.println("_________________________________");
     
     System.out.println("Using a normal for loop (with an if statement):");
		System.out.print("Count is: ");
		
		for (int i=1; i<11; i++) {
			   System.out.print(i);
			 if (i<10) {
			 	System.out.print(", ");
			}
               
          }		
		
		System.out.println("");
		System.out.println("_________________________________");
		System.out.println("Yay it works =)");
	}
}


```

---

### Post by LaRoza on 2008-02-13
<never mind>

---

### Post by sloggerkhan on 2008-02-13
At my school we use eclipse. I'm kinda ambivilant about it because there are things I like, things I don't like.

---

### Post by nhandler on 2008-02-13
Another relatively simple program is BlueJ. It doesn't have a native linux version, but the .jar version ([http://www.bluej.org/download/files/bluej-221.jar](http://www.bluej.org/download/files/bluej-221.jar)) will run just fine. It may be a little slow depending on your system, but it is a simple program to work with. It is able to run and compile java programs. It can execute terminal based programs, applets, and java applications. It also has source code indenting and highlighting.

---

### Post by Abild on 2008-02-13
It works for me if i remove String args[] in main2 (Its only needed in the main function in order to enable your program to accept command line options).

With respect to Java being an object oriented language i would rewrite the program in the following way;

```

public class untitled {

	public static void main (String args[]) {
		untitled untld = new untitled();
		untld.run();
	}
	
	public void run(){
		System.out.println("Using a normal for loop:");
		System.out.print("Count is: ");
		
		for (int i=1; i<11; i++) {
               System.out.print(i);
               System.out.print(", ");
          }		
		
		System.out.println("");
		System.out.println("_________________________________");
		
		int[] numbers = {1,2,3,4,5,6,7,8,9,10};
		System.out.println("Using an array:");
		System.out.print("Count is: ");
          for (int item : numbers) {
            System.out.print(item);
               System.out.print(", ");
          }
        
        System.out.println("");  
        System.out.println("_________________________________");
          
		cont();        
	}
	
	private void cont () { // Make this public if you want 
			//this method to be visible outside this class 
		System.out.println("Now a nested for loop =P");  
        for (int i=1; i<5; i++) {
        	for (int j=1; j<5; j++) {
        		System.out.print(i);
        		System.out.print(" ");
        		System.out.print(j);
        		System.out.print(", ");
			}
		}
		System.out.println("");
		System.out.println("_________________________________");
		
		System.out.println("Now let's try and get rid of that annoying comma at the end of lines using an if statement =)");
		
		System.out.println("But first we must check we can do if statements...");
		int k = 10;
		
		 if (k >= 10) {
          System.out.println("k = 10");
     }
     System.out.println("_________________________________");
     
     System.out.println("Using a normal for loop (with an if statement):");
		System.out.print("Count is: ");
		
		for (int i=1; i<11; i++) {
			   System.out.print(i);
			 if (i<10) {
			 	System.out.print(", ");
			}
               
          }		
		
		System.out.println("");
		System.out.println("_________________________________");
		System.out.println("Yay it works =)");
	}
}

```
And finally, a common coding convention in Java says that class names should be capitalized. It makes it a bit easier to distinguish classes from methods :)

---

### Post by dwally89 on 2008-02-13
Thanks :-)

---

### Post by macogw on 2008-02-13
> **piousp said:**
> Sure, u can use gedit to write your programs, and then compile them with javac, but, at least for me, its more fun to use an IDE. And true, netbeans is more for big projects than just simple apps. BTW, i cant think of a good simple IDE :confused:

Sorry, i didn't meant to sound/be rude. English is not my first language and i just read what i wrote and it kinda sounds rude. :P
What i was trying to say, is that i've only wirk with netbeans and eclipse (command line and basic text editors too :P), therefor, i dont know if there are any IDE for making small apps.

Well, as far as "good, simple IDE" goes, we used BlueJ when learning in school.  It is definitely very simple.  It's practically a text editor and a compile button, but it does have a debugger, and the way it lays out your program as a UML diagram is pretty nice to get a quick visual representation of what on Earth is going on there.

---

