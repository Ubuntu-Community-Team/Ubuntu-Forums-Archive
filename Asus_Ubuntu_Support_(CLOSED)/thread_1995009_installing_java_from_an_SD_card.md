---
title: "installing java from an SD card"
date: 2012-06-03
forum: Asus Ubuntu Support (CLOSED)
---

### Post by halfhearted on 2012-06-03
I am trying to [install java from here]("http://www.java.com/en/download/linux_manual.jsp?locale=en") because my version of Firefox (the 'Help' screen says it is Firefox 12) has completely disabled jave and I need it to access some web sites. There are messages on the web that say that Mozilla did this deliberately because some versions of Firefox were running an old java that was a security risk. [The warning is here.]("http://support.mozilla.org/en-US/kb/use-java-plugin-to-view-interactive-contenthttp://") I have downloaded jre-7u4-linux-i586.tar.gz [from here]("http://www.java.com/en/download/linux_manual.jsp?locale=enhttp://"). I'd like to install it but I am using Ubuntu 12.04 LTS on an Asus EeePC 901. This has one 4GB SD card that the system is on and this is pretty much full up. It also has one slower 8.1GB SD card, so I can put the tar file on it and install from there. Specifically I'm going to put it here /media/ff825a29-b4a6-4fe2-b3c8-d7d755a0ad6e/user1/Java. The problem is that I can't find a set of commands that will run from the terminal to properly install the tar. Does anyone have a foolproof set of steps? I am the fool. Sorry to be long winded.

---

### Post by Paddy Landau on 2012-06-03
I don't understand why you are having problems. The standard Firefox installation on Ubuntu does *not* disable Java. It should just work.

Go to the Ubuntu Software Centre and search for *Ubuntu restricted extras*. Install it if not already installed.

Also search for openjdk. Version 6 should be already installed. (You can try installing version 7, but I don't know whether or not that works.)

---

### Post by halfhearted on 2012-06-05
I don't understand why you don't understand why I'm having problems. Read this message from Mozilla -
[http://support.mozilla.org/en-US/kb/use-java-plugin-to-view-interactive-content?s=to+view+interactive+content&r=0&e=es&as=s](http://support.mozilla.org/en-US/kb/use-java-plugin-to-view-interactive-content?s=to+view+interactive+content&r=0&e=es&as=s)
Now, are you suggesting that when Mozilla says that they _have_ disabled some older versions of Java they are actually lying? Why would they lie about their own product? I don't understand. What would their motivation be? When I run the Java tester that Mozilla recommends lower down the page from Java.com it tells me that Java is not working. Seems to me **it couldn't be clearer**. Back to the question - does anyone know how to install the tar under the circumstances I am working in? Thanks for any assistance.

---

### Post by Paddy Landau on 2012-06-05
> **halfhearted said:**
> I don't understand why you don't understand why I'm having problems. ...
You misunderstand me. I didn't say you shouldn't be having problems; I said that I was not understanding how you had the problem. The problem lies with me, not with you.

As I said, Java should "just work" out of the box; you shouldn't have to install it manually.

Did you try installing Ubuntu Restricted Extras?

---

### Post by halfhearted on 2012-06-05
Ubuntu restricted Extras didn't help. Java wont work if it has been disabled by Mozilla. And they are saying that that is what they have done, for some earlier versions. Here's a good test to see how well **your** Java is working. Many theatres sell seats using Java applets which let you see the layout of the theatre and pick a specific seat. This is the Schiller Theater, part of the Staatsoper in Berlin (where I am incidentally) -
[http://tickets.staatsoper-berlin.de/dsob.webshop/webticket/selectseat;jsessionid=38172F6C6BCEA72E04DA949D065A1DC2?sessionParam=com.eventim.phoenix.domain.SessionParam%4015b6b45%5B38172F6C6BCEA72E04DA949D065A1DC2%5D&tokenName=CSRFTOKEN&languages=%5BLjava.lang.String%3B%409d44ee&processManager=org.apache.velocity.app.FieldMethodizer%40df9d74&event=8653](http://tickets.staatsoper-berlin.de/dsob.webshop/webticket/selectseat;jsessionid=38172F6C6BCEA72E04DA949D065A1DC2?sessionParam=com.eventim.phoenix.domain.SessionParam%4015b6b45%5B38172F6C6BCEA72E04DA949D065A1DC2%5D&tokenName=CSRFTOKEN&languages=%5BLjava.lang.String%3B%409d44ee&processManager=org.apache.velocity.app.FieldMethodizer%40df9d74&event=8653)
When you load this in your browser you should see the animation that shows Java loading followed by the seating layout for this theatre. If your Java is not working you'll get an error message which says, in German - "Your Java is not enabled or the version you are using is outdated! For use of our hall plan, you need Java, unfortunately this could not be started on your system. Please check that your Java is disabled and use the latest version. No Java or install updates necessary? For more information and the required download click here!" If you are using Ubuntu and you can see the seating plan then all is well with your Java. If you get the warning message then you have the same problem I do.

---

### Post by QIII on 2012-06-05
Trying to install Oracle Java from source is unnecessary.  See link in my signature.  You will get the appropriate browser plugin if the site you are trying to view does not recognize the IcedTea plugin.

---

### Post by Paddy Landau on 2012-06-06
> **halfhearted said:**
> Ubuntu restricted Extras didn't help. ...  the Schiller Theater
The link you gave seems to have expired. I tried this instead:
[http://tickets.staatsoper-berlin.de/dsob.webshop/webticket/selectseat?eventId=8770](http://tickets.staatsoper-berlin.de/dsob.webshop/webticket/selectseat?eventId=8770)
Both Firefox and Chromium complained that the script was taking too long.

However, if I go directly to [http://tickets.staatsoper-berlin.de/]("http://tickets.staatsoper-berlin.de/dsob.webshop/webticket/selectseat?eventId=8770"), I get an applet that works correctly (albeit that it is not a useful applet). Also, if I search for Java games, they play correctly. Example: [http://www.darkfish.com/turncoat/](http://www.darkfish.com/turncoat/)

So, It looks to me as though there is something different about the Schiller Theatre. Sorry; this has hit the limits of my knowledge. Perhaps [post=12001797]QIII's post[/post] will help you.

---

### Post by halfhearted on 2012-06-06
Paddy Landau, please read Post #1 in the thread that QIII has kindly supplied in his sig link.

[http://ubuntuforums.org/showthread.php?p=12002898#post12002898](http://ubuntuforums.org/showthread.php?p=12002898#post12002898)

This will disabuse you of the fantasy that "Java works out of the box!" in Ubuntu linux and start to explain the confusion that currently exists. Thank you for your help QIII - I think on balanace I will do it my way - if I can find an answer to my OP.

---

### Post by Paddy Landau on 2012-06-06
> **halfhearted said:**
> Paddy Landau, please read Post #1 in the thread that QIII has kindly supplied in his sig link.
Thank you, that certainly does clear up some confusion. Now I understand why you and I get different results.

Hmm, what a shame that Oracle has removed the license for Java. It may be an idea to contact Schiller's website maintainers and ask them to remove the restriction that only Oracle's Java be allowed.

---

### Post by Paddy Landau on 2012-06-06
Rereading [post=11922462]QIII's post[/post], I realise that his method easily installs both the JRE and the JDK. That should completely solve your problem. Have you tried it yet?

---

### Post by QIII on 2012-06-06
The answer to your OP:  Mozilla has disabled support for older, less secure versions of the Sun Java plugin, not for Oracle Java entirely.  It is as straight forward as that.

This does not strike me as confusing in any way.

---

