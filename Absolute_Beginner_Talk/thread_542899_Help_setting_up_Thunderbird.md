---
title: "Help setting up Thunderbird"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-09-04
I was following the instructions [here](http://ypopsemail.com/index.php?name=Sections&req=viewarticle&artid=19&page=1) for setting up an account in Thunderbird, when I got hung up on step 21.  I clicked on the Advanced button, but I didn't see any tabs at all, so of course I couldn't go to the SMTP tab.  I don't know if this is the cause of my problem, but when I try and go to my inbox, I get an error "could not connect to server local host; the connection was refused."

Any help would be greatly appreciated!

---

### Post by alienexplorers on 2007-09-04
are you running Verizon Yahoo?  If so you will not even need to use the smtp tab.  all yahoo mail is sent via POP mail server.

---

### Post by Yes on 2007-09-04
Yes, I am using Yahoo.

---

### Post by alienexplorers on 2007-09-04
it took me about 5 minutes following those directions.  They are very straight forward.  You should have no problems getting thunderbird running.

---

### Post by thelocust on 2007-09-04
I think there talking about the Copies&Folders option. They should be just fine by default. Connection refused usually means that its talking but you have the wrong password.

---

### Post by thelocust on 2007-09-04
Go to Options Select Privacy Then the Passwords Tab Then hit view saved passwords and verify your using the correct one.

---

### Post by alienexplorers on 2007-09-04
Remember the passwords are case sensitive.  If you typed in lowere case you need to type your password in lower case and so on.  You could have also typed in the wrong server when it asked for the pop server.  This is ease to check..  Go to account settings and to the server page and check the server nme for errors.

---

### Post by Yes on 2007-09-04
I'm sorry, but where do I get to Options?

---

### Post by peebly on 2007-09-04
In the UK yahoo is web based or you can use pop.

Have you enabled the pop support at yahoo.

---

### Post by stevebakerj on 2007-09-04
> **Yes said:**
> I'm sorry, but where do I get to Options?
Its Preferences your after:

Edit
Preferences
Privacy
Passwords
Edit Saved Passwords

---

### Post by thelocust on 2007-09-04
Good call on the enabling pop peebly. I didn't think of that.

---

### Post by Yes on 2007-09-04
Well, apparently I can't use POP with Yahoo unless I subscribe, which is not an option.  So I guess that means I can't get to my Yahoo mail through Thunderbird?

---

### Post by thelocust on 2007-09-04
Thats why everyone should use Gmail

---

### Post by str8line on 2007-09-06
Actually the Verizon Yahoo mail still uses SMTP but requires authentication.  

POP3 is incoming.verizon.yahoo.com
SMTP is outgoing.verizon.yahoo.com

---

### Post by Depressed Man on 2007-09-06
> **Yes said:**
> Well, apparently I can't use POP with Yahoo unless I subscribe, which is not an option.  So I guess that means I can't get to my Yahoo mail through Thunderbird?

Look up the webmail extension and the yahoo extension that goes with it. It'll let you downloa d the emails that way. I use it myself. :)

---

### Post by Yes on 2007-09-08
Well, I installed Webmail, and I'm still getting the same error.  Any idea why?

---

### Post by Yes on 2007-09-10
Bump.

---

### Post by Yes on 2007-09-12
Bump.

---

### Post by qpieus on 2007-09-12
> **Yes said:**
> Well, I installed Webmail, and I'm still getting the same error.  Any idea why?
Did you install the yahoo mail extension also? Go to   [http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)
Install directions are at the bottom of that page. Once you have both webmail and the yahoo extensions, then you can set it up using the instructions at

[http://webmail.mozdev.org/setup.html](http://webmail.mozdev.org/setup.html)

I used port 1026 and it worked fine.

There's also a webmail forum at:

[http://groups.google.com/group/thunderbird-webmail-extension/topics](http://groups.google.com/group/thunderbird-webmail-extension/topics)  where you might find some help.

Of course, thelocust was right in a previous post, use gmail instead. Gmail allows pop access, so you don't have to mess around with webmail. I have an invite if you want one.


One note about the yahoo extension. yahoo-1.2.3 is on the page I linked to above. I used to use that version, but then my yahoo mail stopped being downloaded a couple weeks ago. I did some looking in the webmail forum and saw a newer file, yahoo 1.2.3b4. That file fixed my download problem. What happens is that when yahoo changes something in their web interface, the webmail yahoo extension sometimes stops working, then someone comes out with a new extension to fix the problem. Anywho, I notice now that an even newer file, yahoo-1.3.0b2, is shown on the forum page at [http://groups.google.com/group/thunderbird-webmail-extension](http://groups.google.com/group/thunderbird-webmail-extension)
There's a post about a potential problem with yahoo-1.3.0b2 here, but it looks like the guy figured out how to fix it:
[http://groups.google.com/group/thunderbird-webmail-extension/browse_thread/thread/d326ed6833b939d5](http://groups.google.com/group/thunderbird-webmail-extension/browse_thread/thread/d326ed6833b939d5)

---

### Post by Yes on 2007-09-12
I downloaded the yahoo-1.3.0b2, and I get the error that was fixed in your second link.  The guy says that he fixed the problem by "changing the requirement to 1.2.5b1"...How would I do that?  

Thanks.

---

### Post by qpieus on 2007-09-13
There are some new posts in that thread today. Here's a quote from one of the new posts> Extract the "install.rdf" file from the XPI (it is a zip file), and
edit the <em:minVersion> for the web-mail extension.  Then update the
XPI and install. 

Also I see there's a newer file too:   1-3-0b3

Maybe that one has the fix already in it....

[http://groups.google.com/group/thunderbird-webmail-extension/files](http://groups.google.com/group/thunderbird-webmail-extension/files)

---

### Post by Yes on 2007-09-13
Ok, I installed that, everything seems to be working...but I still get the same error.  Do you know what the problem might be?

Thanks.

---

### Post by Yes on 2007-09-15
Well, I got it to download my emails, but not I can't send any emails from Thunderbird, and when I go into my Yahoo inbox, my inbox is empty.  Any idea why?

Thanks.

---

