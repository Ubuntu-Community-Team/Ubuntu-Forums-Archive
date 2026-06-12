---
title: "[SOLVED] MS Access Alternet"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Xoanan on 2007-05-03
Hi All

Are there any Linux/Ubuntu alternates to this program?  I use it a bit in the office

Just wondering:popcorn:

---

### Post by darkrose on 2007-05-03
OpenOffice Base is the most popular/common, there's a few other but i can't recall them off the top of my head.

---

### Post by darren1270 on 2007-05-03
Open office has a full suite of products... haven't used that much yet but go here and it will tell you about it.
[http://www.openoffice.org/product/](http://www.openoffice.org/product/)

---

### Post by dergringo on 2007-05-03
I'm not sure but I think Open Office Base doesn't come with an own database engine like Access does. It's afaik just a frontend to other database engines like mysql, mssql, access and so on.

You could give kexi a try: [http://www.kexi-project.org/](http://www.kexi-project.org/) :)

Greetings

Philipp

---

### Post by mediax on 2007-05-03
> **dergringo said:**
> I'm not sure but I think Open Office Base doesn't come with an own database engine like Access does. It's afaik just a frontend to other database engines like mysql, mssql, access and so on.

Having had a quick look at the specs, Base does seem to include its own database engine - it's not just a front-end, although it does allow access to other tables (in much the same way as Access does).

---

### Post by steve.horsley on 2007-05-03
Base makes heavy use of java. And it doesn't seem to see the version if java that Ubuntu installs by default. You would be better off installing Suns Java Runtime Environment. Then select this in the OOo Tools->Options->Java dialog.

Base does have its own internal database engine so that you can save a complete database as a .odb file (as Access does). It also front-ends any number of other databases, simply by installing the appropriate JDBC driver.

---

### Post by Xoanan on 2007-05-03
Thanx all for your answers!  I really appreciate the help!:)

---

### Post by Xoanan on 2007-05-04
Hi There
Regarding Java;  I found it in the synaptic package manager, but I have to go through EULA in order to install it, which I apparently cannot do through synaptic because it hangs on that "I accept" page.  How do I work around that?

---

### Post by mcduck on 2007-05-04
> **Xoanan said:**
> Hi There
Regarding Java;  I found it in the synaptic package manager, but I have to go through EULA in order to install it, which I apparently cannot do through synaptic because it hangs on that "I accept" page.  How do I work around that?
Just hit tab key to get to the 'I Accept'-button & press Enter. :)

---

### Post by Xoanan on 2007-05-06
Still having issues installing Java;  the dialog tells me that it must be owned by root;  I might need to use apt -get but I am not experienced at that;  Any ideas:confused:

---

### Post by starcraft.man on 2007-05-06
Ok, easy enough: Open up the terminal , Applications > Accessories > Terminal.

Then type in this:

```
sudo aptitude install sun-java6-bin sun-java6-jre sun-java6-plugin
```

If you get a blue screen asking EULA, just push tab till yes is select and push enter :)

That should solve your problem :)

---

### Post by boudreaujr on 2007-05-06
From a terminal window run

sudo apt-get install *program name*

That should get you through any installation that requires root access.  Don't be afraid of the terminal or using these commands.  They become invaluable in fixing problems or finding specific information as time goes on.


Good luck.

Denis

---

### Post by Xoanan on 2007-05-06
Ah, thanx
I think I found the issue;  the problem was I didnt have the j2sdk 1.4.2 doc.zip in that;  I had to download it and place it in the temp folder;  After that, I didn have any further issues with installation.  Now lets see if that helps me out on OO....:popcorn:

---

### Post by Xoanan on 2007-05-06
Here is something odd; this has been occurring on other programs as well; its a strange scrambled border that obscures some of the minimize/maximize/close icons and also the title

---

