---
title: "Exception in thread &quot;main&quot; java.lang.NoClassDefFoundError:"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-11-20
Hey guys. I just installed the JDK, and programs compile correctly, but when I go to run them, I get this error: 
```

Exception in thread "main" java.lang.NoClassDefFoundError:
```

I did not set up anything after the installation, so I'm not sure if I do or not. I know I need to on Windows, but not sure about Ubuntu. Thanks!

---

### Post by stchman on 2007-11-20
> **drndrw said:**
> Hey guys. I just installed the JDK, and programs compile correctly, but when I go to run them, I get this error: 
```

Exception in thread "main" java.lang.NoClassDefFoundError:
```

I did not set up anything after the installation, so I'm not sure if I do or not. I know I need to on Windows, but not sure about Ubuntu. Thanks!

Sounds like a Java coding problem not an Ubuntu problem.  Post your java code and let us look at it.

---

### Post by Inxsible on 2007-11-20
your main method is trying to reference a class which does not exist. There's nothing much anyone can help unless they see the code :)

---

### Post by drndrw on 2007-11-20
Okay, well I was actually using two different ones. One was straight out of a book, so it really should work. Anyways, this is what I used:

```
class DayCounter {
    public static void main(String[] arguments) {
        int yearIn = 2008;
        int monthIn = 1;
        if (arguments.length > 0)
            monthIn = Integer.parseInt(arguments[0]);
        if (arguments.length > 1)
            yearIn = Integer.parseInt(arguments[1]);
        System.out.println(monthIn + "/" + yearIn + " has "
            + countDays(monthIn, yearIn) + " days.");
    }

    static int countDays(int month, int year) {
        int count = -1;
        switch (month) {
            case 1:
            case 3:
            case 5:
            case 7:
            case 8:
            case 10:
            case 12:
                count = 31;
                break;
            case 4:
            case 6:
            case 9: 
            case 11:
                count = 30;
                break;
            case 2:
                if (year % 4 == 0)
                    count = 29;
                else
                    count = 28;
                if ((year % 100 == 0) & (year % 400 != 0))
                    count = 28;
        }
        return count;
    }
}
```

---

