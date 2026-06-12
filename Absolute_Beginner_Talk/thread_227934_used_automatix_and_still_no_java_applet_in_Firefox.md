---
title: "used automatix and still no java applet in Firefox"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by Handyman's Special on 2006-08-02
Downloaded Automatic and used it to install Java.

There is an icon for a Java Control Center in  Applications\System tools but the icon is blank.

When I go to Add\Remove and click on Sun Java this is what I get:
[b]'sun-java5-bin' is not available in any software channel.

The application might not support your system architecture[/b]

There are only two issues remaining to be resolved to make my Ubuntu OS a completely satusfactory deal. The Java applet in Firefox and getting my digital camera accepted for downloading pictures.

I am open for help with the java. I have downloaded so much stuff my head swims when I try to figure it out. I have read so many posts on how to get it working they are all running together in my head. I am on dial-up and downloading the 'extra' cd is daunting to say the least. It took days to get Ubuntu itself. Is that the only way to get the java?

regards,
HS

---

### Post by confused57 on 2006-08-02
May be something in this thread that will help:

[http://ubuntuforums.org/showpost.php?p=1231275&postcount=5](http://ubuntuforums.org/showpost.php?p=1231275&postcount=5)

---

### Post by zxee on 2006-08-02
I'm on dial up also so I can sympatize. Do you have the restricted repos enabled in /etc/apt/sources.list? If not uncomment them and then run > sudo apt-get update Hope that helps.
For the camera issue you may want to start a new thread-there are also many threads on getting digital cameras recognized.

---

### Post by moma on 2006-08-02
Can you list the content of these: 

What is the location of Firefox?  (the -> link will reveal that). Default location is /usr/lib/firefox.
$ [COLOR="Green"]ls -l /usr/bin/firefox[/COLOR]
or maybe better to say 
$ [COLOR="Green"]readlink -f /usr/bin/firefox[/COLOR]

Automatix (or plugin-packages) do not check this and they copies all plugins to /usr/[COLOR="Red"]lib[/COLOR]/firefox/plugins. FYI: Some people prefers to install programs to /usr/local/ which is a more natural location. 

Can you see libjavaplugin.so in the plugins folder?  Is it linked to some other library?
$  [COLOR="Green"]ls -l /usr/lib/firefox/plugins/[/COLOR] 

Restart Firefox after you have installed Java (JRE).

You can test your browser plugins by following the Step 7) here
[http://www.futuredesktop.net/ubuntu6.06.html]("http://www.futuredesktop.net/ubuntu6.06.html")

---

### Post by Handyman's Special on 2006-08-02
> **moma said:**
> Can you list the content of these: 

What is the location of Firefox?  (the -> link will reveal that). Default location is /usr/lib/firefox.
$ [COLOR="Green"]ls -l /usr/bin/firefox[/COLOR]
or maybe better to say 
$ [COLOR="Green"]readlink -f /usr/bin/firefox[/COLOR]

Automatix (or plugin-packages) do not check this and they copies all plugins to /usr/[COLOR="Red"]lib[/COLOR]/firefox/plugins. FYI: Some people prefers to install programs to /usr/local/ which is a more natural location. 

Can you see libjavaplugin.so in the plugins folder?  Is it linked to some other library?
$  [COLOR="Green"]ls -l /usr/lib/firefox/plugins/[/COLOR] 

Restart Firefox after you have installed Java (JRE).

You can test your browser plugins by following the Step 7) here
[http://www.futuredesktop.net/ubuntu6.06.html]("http://www.futuredesktop.net/ubuntu6.06.html")

Hello,

Below is what I get after entering each of the commands you posted.
bash: $: command not found

I will follow step 7 and see what I get.

Thanks for taking the time to look at this problem. What you are saying makes sense. Would that explain the 'blank' icon for the Java control center?

Regards,
HS

---

### Post by moma on 2006-08-03
Do not write the "$", it denotes a command prompt.
Write the command only.

---

### Post by Handyman's Special on 2006-08-03
Hi moma,

Feeling pretty dumb here! Many thanks for your patience!!!!

Here are the results:
lrwxrwxrwx 1 root root 22 2006-07-29 13:20 /usr/bin/firefox -> ../lib/firefox/firefox


/usr/lib/firefox/firefox

total 12
-rw-r--r-- 1 root root 8652 2006-07-27 11:00 libunixprintplugin.so

I went to the URL and followed their directions. I could not 'see' the java applet they had in their example but when I went to another of the spots they called for, it was reported that I did have Java installed. I went into the section of my firefox that controls java and there is a very long list of 'Errors' for java applets. Would you need to see some of it?

Can't say enough how much I appreciate any time you have spent considering this mess.=D> 

Later,
Handyman's Special

---

### Post by not_yet on 2006-08-03
locate your firefox plugin folder

locate java folder

make a symlink from the firefox plugin folder to libjavaplugin_oji.so

use the terminal, navigate to the firefox plugin folder and

ln -s  /to where java libjavaplugin_oji.so lives

---

### Post by moma on 2006-08-03
Hello Handyman

Your /usr/lib/firefox/plugins directory seems to be almost empty.

$ [COLOR="Green"]ls -l /usr/lib/firefox/plugins[/COLOR]
> **Handyman's Special said:**
> 
total 12
-rw-r--r-- 1 root root 8652 2006-07-27 11:00 libunixprintplugin.so


My recommendation is this:
Download BUMPS script from 
[http://ubuntuforums.org/showthread.php?t=181251]("http://ubuntuforums.org/showthread.php?t=181251")
Bumps is similar to Automatix and EasyUbuntu.

Create a "bumps" directory in your $HOME-folder. 
Download "bumps 1.3.tar.gz" and unzip the package there.

$ [COLOR="Green"]cd bumps[/COLOR]

$ [COLOR="Green"]ls -l[/COLOR]
and you should see this 
> [SIZE="1"]total 28
-rwxr-xr-- 1 moma moma 4341 2006-07-05 19:08 bumps
-rw-r--r-- 1 moma moma 3512 2006-08-03 18:22 bumps.log
-rw-r--r-- 1 moma moma 4749 2006-07-06 02:19 changelog
-rw-r--r-- 1 moma moma 2982 2006-07-04 14:50 readme
-rw-r--r-- 1 moma moma 1270 2006-07-04 14:51 sources.list.bumps[/SIZE]
Start the bumps-script
$ [COLOR="Green"]sudo ./bumps[/COLOR]

Restart Firefox after it's completed.

**BTW**: Write ```
[COLOR="Red"]about:plugins[/COLOR]
``` in the Firefox' address bar and it will report all the installed add-ons.

---

### Post by Kilgore_Trout on 2006-08-08
not_yet,

I have been having a similar problem, and I think your advice above might help me...

I have located libjavaplugin.so in usr/lib/**mozilla-firefox**/plugins

But it seems that firefox uses the plugins located in usr/lib/**firefox**/plugins.

I would like to make a symlink to the libjavaplugin.so file from the ../firefox/plugins folder, but I am not sure how to navigate to this folder in the terminal. Can you help out with this step? 

TIA

---

### Post by tosk on 2006-08-08
The */usr/lib/mozilla-firefox* folder is just a symlink to the */usr/lib/firefox* folder.

I've found that the steps below install the plugin easily enough:

[LIST=1]
[*]Make sure the JRE is installed properly (the **sun-java5-jre** package).
[*]Type the line you see below into the Terminal.
[*]Restart Firefox.
[/LIST]
```
# Add the line below in the Terminal
sudo ln -s /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so
# End code snippet
```

When you're back in Firefox, type **[COLOR="Navy"]about:plugins[/COLOR]**. Java should be listed there.

---

### Post by xpod on 2006-08-08
Not sure if this helps but a lot of digital cameras have 2 options on pc`s.
One usually allows you to take photos and video directly on to your pc via usb .
And the other would be the setting for uploadind photo`s taken separate from pc.
None of mine show up(yet)for pc connected photo taking but if i switch them over for uploading they automatically show up on the desktop..without ever having had to get some extra app etc.
Mabey you could try and see??

---

