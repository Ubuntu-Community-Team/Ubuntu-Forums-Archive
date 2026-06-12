---
title: "Few java questions"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-07-21
These are command help:

Anyone have some code i can put like er heres my entire java so far:

```

public class Launcher {
	public static void main(String[] args) {
	try {
	System.out.println("==============================");
	System.out.println("Endar V4");
	System.out.println("===");
	System.out.println("Made by Goat Spirit");
	System.out.println("===");
	System.out.println("endar@goat-spirit.com");
	System.out.println("===");
	System.out.println("Expect 5 Second Pauses In Between Each Screen.");
	System.out.println("==============================");
	Thread.sleep(2000);
	} catch(InterruptedException ex) {
	System.out.println("Sorry, Endar V4 Could Not Start Up.");
	System.out.println("Post Your Error Here:");
	System.out.println("http://goat-spirit.com/endar/index.php");
	}
	}
}

```

I need a code that will go in like er....will change directorys to files, then execute another class file, thiss possible?

---

### Post by Ben Sprinkle on 2006-07-21
any1?

---

### Post by JoshHendo on 2006-07-21
You only have text. That is just going to print out. It is a pre-set error. You need other things, like if.. else statements, try and catch etc.

You do know about those things don't you?

Anyway, when you want to change directorys, make it relevant to the directory that class file is in. For example, I have a file with test.class in it. In the folder "folder1", there is a file called test2.class. To access text2.class from test.class, it would be "folder1/test2.class".

- Josh

---

