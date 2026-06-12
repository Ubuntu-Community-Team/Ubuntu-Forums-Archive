---
title: "[SOLVED] Firefix won't hold unicode as default"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-03-05
Greetings.

Part of my PC life is working in Foreign alphabets which involves viewing in unicode;
View/character encoding/unicode (UTF-8 ). Trouble is, it keeps reverting to the adjacent one, Western, and I have to select unicode option _every time_, which reaches the point of becoming annoying.

It is especially regretful for me to say that in Windows, Internet Explorer holds the encoding viewing option once they are selected.

kind regards

John

---

### Post by PapaNerd on 2008-03-12
Try adding the line:
user_pref("intl.charset.default", UTF-8);
to your /home/<username>/.mozilla/firefox/*.default/user.js file and then re-start your browser.

---

### Post by Andavane on 2008-03-12
> **PapaNerd said:**
> Try adding the line:
user_pref("intl.charset.default", UTF-8);
to your /home/<username>/.mozilla/firefox/*.default/user.js file and then re-start your browser.
Thank you.
However when I go

home/andavane/

there is no .mozilla folder listed.

What am I doing wrong?

John

---

### Post by Achtung on 2008-03-12
The "." in front of the folder name denotes a hidden folder. Press Ctrl+H to reveal hidden folders, or simply type the name directly in the location bar (Press the "Pencil and paper" icon on the left if buttons representing each folder in the current path are where the location bar should be).

---

### Post by PapaNerd on 2008-03-12
Alternately, from a terminal window (Applications > Accessories > Terminal), you should be able to see hidden files and directories by typing "ls -la".  Then, you have the choice of either going down a directory at a time:
cd .mozilla
cd firefox
cd *.default
or all at once:
cd .mozilla/firefox/*.default

If you then do a "ls -l" command, you see the user.js file that needs to have the line added to it.  If you are not comfortable with the editors (such as vi), then just type the line:
echo "user_pref(\"intl.charset.default\", UTF-8);" >> user.js
This will append the line to the file without having to mess around with an editor.

You could also do the file append in one line like this:
echo "user_pref(\"intl.charset.default\", UTF-8);" >> /home/andavane/.mozilla/firefox/*.default/user.js

---

### Post by Andavane on 2008-03-12
> **PapaNerd said:**
> Try adding the line:
user_pref("intl.charset.default", UTF-8);
to your /home/<username>/.mozilla/firefox/*.default/user.js file and then re-start your browser.
Well thank you please bear with me, as I am on a learning curve here.
I understood the bit about seeing the ./ files.

Now in the chain

> /home/<username>/.mozilla/firefox/*.default/user.js file

I can open as far as /firefox

but when I go further and open the firefox folder it says:

'ydu3ha8m.defaul't (folder) and 'pluginreg.dat' (file) and 'profiles.ini' (file)

If I open the 'ydu3ha8m.default (folder)' I then get  four more folders and masses and masses of files.

However it is interesting.
I would imagine that when I click an option in the firefox broswer, it writes a command to one on the files.

Am I correct?

Anyway, I would like to go slowly onto the next step. I think I would understand it fully once completing the process.

Regards

John

---

### Post by PapaNerd on 2008-03-12
Yes, you are in the correct directory.  The reason I gave the "*" wildcard in the cd command is because this directory name is different for each user.  The pertinent files in your "ydu3ha8m.default" sub-directory are the ones ending in ".js".  You don't want to touch the "pref.js" or "sessionstore.js" files, as they are written by firefox while it is open and as it closes.  The "user.js" file is where you can program in your preferences for starting up a new session.  The line I supplied will force the character encoding parameter that you want to set.

---

### Post by Andavane on 2008-03-13
> **PapaNerd said:**
> Yes, you are in the correct directory.  The reason I gave the "*" wildcard in the cd command is because this directory name is different for each user.  The pertinent files in your "ydu3ha8m.default" sub-directory are the ones ending in ".js".  You don't want to touch the "pref.js" or "sessionstore.js" files, as they are written by firefox while it is open and as it closes.  The "user.js" file is where you can program in your preferences for starting up a new session.  The line I supplied will force the character encoding parameter that you want to set.

Well, PapaNerd "prefs.js" and "sessionstore.js" are the only *.js files I can see in my list,
[sic]:

> -rw-r--r-- 1 andavane andavane     742 2008-03-13 09:41 blocklist.xml
drwx------ 2 andavane andavane    4096 2008-03-13 05:58 bookmarkbackups
-rw-r--r-- 1 andavane andavane  154494 2008-03-13 21:13 bookmarks.bak
-rw-r--r-- 1 andavane andavane  154494 2008-03-13 21:13 bookmarks.html
drwxr-xr-x 2 andavane andavane   20480 2008-03-13 21:17 Cache
-rw------- 1 andavane andavane   65536 2008-03-13 13:54 cert8.db
drwxr-xr-x 2 andavane andavane    4096 2008-02-06 18:45 chrome
-rw------- 1 andavane andavane     126 2008-02-08 05:15 compatibility.ini
-rw-r--r-- 1 andavane andavane  133623 2008-03-08 17:42 compreg.dat
-rw------- 1 andavane andavane  115408 2008-03-13 21:18 cookies.txt
-rw-r--r-- 1 andavane andavane     206 2008-03-13 07:49 downloads.rdf
drwxr-xr-x 3 andavane andavane    4096 2008-03-13 09:41 extensions
-rw-r--r-- 1 andavane andavane     331 2008-03-08 17:42 extensions.cache
-rw-r--r-- 1 andavane andavane     331 2008-03-08 17:42 extensions.ini
-rw-r--r-- 1 andavane andavane    3939 2008-03-08 17:42 extensions.rdf
-rw-r--r-- 1 andavane andavane   86073 2008-03-13 13:54 formhistory.dat
-rw-r--r-- 1 andavane andavane  154873 2008-03-13 07:00 foxmarks-baseline-9deeda96bd35b826.json
-rw-r--r-- 1 andavane andavane  474230 2008-03-13 21:11 foxmarks.log
-rw-r--r-- 1 andavane andavane 2879007 2008-03-13 21:18 history.dat
-rw------- 1 andavane andavane     201 2008-03-06 04:38 hostperm.1
-rw-r--r-- 1 andavane andavane    1394 2008-03-08 16:49 install.log
-rw------- 1 andavane andavane   16384 2008-03-13 13:54 key3.db
-rw-r--r-- 1 andavane andavane   13349 2008-03-13 21:14 localstore.rdf
lrwxrwxrwx 1 andavane andavane      15 2008-03-13 17:09 lock -> 127.0.1.1:+5946
-rw-r--r-- 1 andavane andavane    4800 2008-03-13 07:49 mimeTypes.rdf
-rw-r--r-- 1 andavane andavane   23187 2008-03-13 13:54 prefs.js
-rw-r--r-- 1 andavane andavane    3287 2008-02-06 18:45 search.rdf
-rw-r--r-- 1 andavane andavane    2048 2008-02-06 18:45 search.sqlite
-rw------- 1 andavane andavane   16384 2008-02-06 18:45 secmod.db
-rw------- 1 andavane andavane   94784 2008-03-13 21:18 sessionstore.js
-rw------- 1 andavane andavane    4509 2008-03-07 17:24 signons2.txt
-rw-r--r-- 1 andavane andavane 3055616 2008-03-13 21:15 urlclassifier2.sqlite
-rw-r--r-- 1 andavane andavane 1741328 2008-03-06 04:39 XPC.mfasl
-rw-r--r-- 1 andavane andavane  103659 2008-03-08 17:42 xpti.dat
-rw-r--r-- 1 andavane andavane 1063677 2008-03-12 20:00 XUL.mfasl
[email]andavane@andavane-desktop:~/.mozilla/firefox/ydu3ha8m.defa[/email]ult$ 


and those are the ones I don't want to touch. So Ihave seemed to reach an impasse again.
But it has been interesting seeing thus far.

Can you put me right?

Regards

John

---

### Post by PapaNerd on 2008-03-14
Did you enter the command to add the preference?  The syntax I supplied should have either appended the preference to an existing user.js file or created a new file with just the single preference line in it.

---

### Post by Andavane on 2008-03-14
> **PapaNerd said:**
> Did you enter the command to add the preference?  The syntax I supplied should have either appended the preference to an existing user.js file or created a new file with just the single preference line in it.
No Sir I just used the command line and cd to get down there and see the files, then printed the list.
Will read your instructions again.
Hopefully the penny will drop.
Regards
John

---

### Post by Andavane on 2008-03-14
> **PapaNerd said:**
> Alternately, from a terminal window (Applications > Accessories > Terminal), you should be able to see hidden files and directories by typing "ls -la".  Then, you have the choice of either going down a directory at a time:
cd .mozilla
cd firefox
cd *.default
or all at once:
cd .mozilla/firefox/*.default

If you then do a "ls -l" command, you see the user.js file that needs to have the line added to it.  If you are not comfortable with the editors (such as vi), then just type the line:
echo "user_pref(\"intl.charset.default\", UTF-8);" >> user.js
This will append the line to the file without having to mess around with an editor.

You could also do the file append in one line like this:
echo "user_pref(\"intl.charset.default\", UTF-8);" >> /home/andavane/.mozilla/firefox/*.default/user.js

Well yes, as I said, I've been through it again, and yes it is just as you say the "user.js" file has been created, and in it is the command

> user_pref("intl.charset.default", UTF-8);

and yes when I open firefox it now gives me the Unicode default as UTF-8, just as I wanted it to, so
Many Thanks.
You know I feel I could really get to like this stuff!

I deduced by the way that it is the ">>" bit which created the new file.

Best wishes
John

---

### Post by PapaNerd on 2008-03-15
You are welcome.  Glad to be able to help out.

Yes, the ">>" takes the output of the echo command and appends it into a file.  Similarly, using ">" would have placed the output into a file, but also would have wiped out any existing data had file already been present.  Also, you'll note the extra "\" in front of the second and third quotes in the command line which prevented them from terminating the echo command, but instead placed the quotes into output stream and thus into the file.

If you do a web search for "mozilla hidden preferences", you should find a lot of pages talking about preferences you can set.  The UTF-8 preference wasn't documented on any of the pages I found, but an educated guess on the syntax and one empirical test helped me figure it out for you.  Incidentally, I use the user.js preference files to bring my browser back to a known state each time I open it up, and also whenever I reinstall the operating system to quickly configure my mozilla applications.

---

### Post by Andavane on 2008-03-15
Thank you again. Very interesting.
I wonder if I could squeeze another question in here.
When I scan a doc with Xsane I want it to be saved into the folder I want, not all over the home directory.
Looking at he hidden folders I see there is a folder called '.sane'; and in that folder is another folder called xsane., and in THAT folder I see:

> batch-lists  Epson:Perfection610.drc  xsane.mdf  xsane.rc

but no obvious way of saving my scan into my 'CScans' folder which is where I want them to be saved.

I did raise this query last July, viz:
[http://ubuntuforums.org/showthread.php?t=509201]("http://ubuntuforums.org/showthread.php?t=509201")

but have not made much progress, i.e. I haven't yet found out how to save every scan without altering the path every time.

Kind regards

John

---

### Post by PapaNerd on 2008-03-15
I don't know the answer to that, but suggest you start a new thread, otherwise it likely will not be widely seen by others.

---

### Post by Andavane on 2008-03-15
Thanks again.
I'll do that.
John

---

