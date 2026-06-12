---
title: "firefox download manager edit actions trouble"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by phil54601 on 2007-02-13
Hello;
I am unable to edit any actions under 'edit | preferences | Downloads | view & edit actions'.  I have downloaded a number of '.jpg' files, but nothing is listed for 'actions' or 'file types'.  If I remember correctly that dialog box contains file types of files that I have already downloaded.  Do I need to re-install firefox?
Thanks
Phil

---

### Post by LotsOfPhil on 2007-02-13
In Firefox, press Ctrl+Y. Is this what you're looking for?

It's in Tools -> Downloads, too...

---

### Post by phil54601 on 2007-02-14
Hello;
I found that.  I use it for ALL downloads.  There is an option in firefox under 'edit | preferences, under the download tab.  That option toward the bottom says 'View & Edit Actions'.  Clicking that link brings up a dialog, but I can't do anything with that dialog.  It's for automating downloads for certain file types. 
Thanks
Phil

---

### Post by Maestro23 on 2007-02-14
> **phil54601 said:**
> Hello;
I found that.  I use it for ALL downloads.  There is an option in firefox under 'edit | preferences, under the download tab.  That option toward the bottom says 'View & Edit Actions'.  Clicking that link brings up a dialog, but I can't do anything with that dialog.  It's for automating downloads for certain file types. 
Thanks
Phil

Edit>>Prefs>>Content>>File Types(Manage)

---

### Post by phil54601 on 2007-02-14
Hello;
I tried to follow your suggestion:
Edit>>Prefs>>Content>>File Types(Manage)
I can only get to content.  I don't see any option - button or tab for 'file' or 'file type', under the content tab.  I only have: 
1.) Block popup windows  (check-box)
2.) warn me when web....install ext or themes  (check-box)
3.) Load Images -- also for the original site  (check-box)
4.) enable java  (check-box)
5.) enable java script  (check-box)
There are buttons for 'allowed sites',  'exceptions' or 'advanced' at the right of the above check-boxes.

6.) fonts section
'help'  & 'close' buttons are at the bottom corners.   I'm using Firefox/1.5.0.9.
Thanks
Phil

---

### Post by LotsOfPhil on 2007-02-14
You were looking in the right place since you have 1.5 ("There is an option in firefox under 'edit | preferences, under the download tab. That option toward the bottom says 'View & Edit Actions'. Clicking that link brings up a dialog, but I can't do anything with that dialog. It's for automating downloads for certain file types.")

I had a similar problem and had to go into ~/.mozilla/firefox/blabla/mimeTypes.rdf and manually edit it.
Replace 'blabla' with some random string, you'll see what it is.

As far as what to change, you were having problems with jpegs, right? Try and find the offending file type and mess around. 
You should probably backup the mimeTypes.rdf file first :)

---

### Post by Maestro23 on 2007-02-14
> help' & 'close' buttons are at the bottom corners. I'm using Firefox/1.5.0.9.

You didn't say in you first post, thought you were using 2.0.  Good luck with 1.5 man.

---

### Post by phil54601 on 2007-02-14
Hello;
Sounds like you have the right idea, but I'm too new to Ubuntu to start playing around in a system file without detailed instructions on what I'm looking for & what to do with it once I find it!  I just re-installed about 2 weeks ago, so I am NOT willing to take a chance at messing it up again.  How do I get to '~/.mozilla/firefox/blabla/mimeTypes.rdf'?   I have never seen anything like this (~/.)  before.  The closest is like '.thumb'.
I know nothing about mime type stuff.
Any further suggestions would be appreciated. 
Thanks
Phil

---

### Post by Maestro23 on 2007-02-14
> **phil54601 said:**
> Hello;
Sounds like you have the right idea, but I'm too new to Ubuntu to start playing around in a system file without detailed instructions on what I'm looking for & what to do with it once I find it!  I just re-installed about 2 weeks ago, so I am NOT willing to take a chance at messing it up again.  How do I get to '~/.mozilla/firefox/blabla/mimeTypes.rdf'?   I have never seen anything like this (~/.)  before.  The closest is like '.thumb'.
I know nothing about mime type stuff.
Any further suggestions would be appreciated. 
Thanks
Phil

.mozilla is a hidden directory in your /home/username

cd ~/.mozilla/firefox/et....

Type [COLOR="Red"]pwd [/COLOR]to show where you are at at any given time.

ls = list files in the current directory

*Good site to get your feet wet with commands/file structure: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by phil54601 on 2007-02-14
Hello all;
I'll try to reply to all posts.  All the options to update firefox are greyed out, like under the help menu. I did a search for 'mimeTypes.rdf' the only file was in '/etc/firefox/profile'.  I did select 'show hidden & system files'.   
This is the output from a terminal:
[email]phil@phil-T23:~/.mozi[/email]lla/firefox$ ls
k088dvow.default  pluginreg.dat  profiles.ini
[email]phil@phil-T23:~/.mozi[/email]lla/firefox$
It doesn't look like there are any folders there.
Thanks Phil

---

### Post by LotsOfPhil on 2007-02-14
Almost there! the 'blabla' directory in question is k088dvow.default

If you type cd ~/.mozilla/firefox/k088dvow.default then you will see mimeTypes.rdf

I understand not wanting to mess around with the file. I think this is the only way to do it. I don't know what firefox's problem is. If you post the contents of mimeType.rdf, I'll try and find what you should change.

---

### Post by phil54601 on 2007-02-16
Hello;
Here is the list.  I needed to replace all (<) & (>) with (~)  & the (:D) with (:d) to get past the (8)image limit of a post.  HTML tags are images!

~?xml version="1.0"?~      
~RDF:RDF xmlns:NC="http://home.netscape.com/NC-rdf#"
         xmlns:RDF="http://www.w3.org/1999/02/22-rdf-syntax-ns#"~
  ~RDF:description RDF:about="urn:mimetype:application/pdf"
                   NC:description="PDF document"
                   NC:value="application/pdf"
                   NC:editable="true"~
    ~NC:handlerProp RDF:resource="urn:mimetype:handler:application/pdf"/~
  ~/RDF:description~
  ~RDF:description RDF:about="urn:mimetype:externalApplication:application/x-tar"
                   NC:MrettyName=""   (This is really 'NC:' plus 'prettyName=')
                   NC:path="" /~
  ~RDF:Seq RDF:about="urn:mimetypes:root"~
    ~RDF:li RDF:resource="urn:mimetype:text/x-uri"/~
    ~RDF:li RDF:resource="urn:mimetype:application/x-tar"/~
    ~RDF:li RDF:resource="urn:mimetype:application/pdf"/~
  ~/RDF:Seq~
  ~RDF:description RDF:about="urn:mimetype:externalApplication:application/pdf"
                   NC:prettyName=""
                   NC:path="" /~
  ~RDF:description RDF:about="urn:mimetype:handler:application/x-tar"
                   NC:alwaysAsk="true"
                   NC:useSystemDefault="true"~
    ~NC:externalApplication RDF:resource="urn:mimetype:externalApplication:application/x-tar"/~
  ~/RDF:description~
  ~RDF:description RDF:about="urn:mimetype:externalApplication:text/x-uri"
                   NC:prettyName=""
                   NC:path="" /~
  ~RDF:description RDF:about="urn:mimetype:text/x-uri"
                   NC:value="text/x-uri"
                   NC:editable="true"
                   NC:description="resource location"~
    ~NC:handlerProp RDF:resource="urn:mimetype:handler:text/x-uri"/~
  ~/RDF:description~
  ~RDF:description RDF:about="urn:mimetype:application/x-tar"
                   NC:value="application/x-tar"
                   NC:editable="true"
                   NC:description="tar archive"~
    ~NC:handlerProp RDF:resource="urn:mimetype:handler:application/x-tar"/~
  ~/RDF:description~
  ~RDF:description RDF:about="urn:mimetype:handler:application/pdf"
                   NC:alwaysAsk="true"
                   NC:useSystemDefault="true"
                   NC:saveToDisk="false"~
    ~NC:externalApplication RDF:resource="urn:mimetype:externalApplication:application/pdf"/~
  ~/RDF:description~
  ~RDF:description RDF:about="urn:mimetypes"~
    ~NC:MIME-types RDF:resource="urn:mimetypes:root"/~
  ~/RDF:description~
  ~RDF:description RDF:about="urn:mimetype:handler:text/x-uri"
                   NC:alwaysAsk="false"
                   NC:useSystemDefault="true"~
    ~NC:externalApplication RDF:resource="urn:mimetype:externalApplication:text/x-uri"/~
  ~/RDF:description~
~/RDF:RDF~
  
It looks like it does a lot of repeating.   I noticed lots of entries for 'pdf' & 'tar' and nothing else.  Aren't file types supposed to automatically added when I downlaod a new type.  It's not doing that either.
Thanks
Phil

---

### Post by LotsOfPhil on 2007-02-16
Damn. I see nothing of use in there. We are looking for something dealing with images/jpegs right? I fear I have wasted both of our time :(

---

### Post by phil54601 on 2007-02-17
Hello;
Wouldn't just removing & re-installing firefox fix everything?
Thanks 
Phil

---

### Post by LotsOfPhil on 2007-02-17
Maybe. Go for it if you're so inclined.

---

### Post by phil54601 on 2007-02-22
Hello;
I did an uninstall & reinstall, but didn't shut down in between.  It only partly fixed the problem.  WMV is now listed, but not jpg or jpeg.
Thanks
Phil

---

### Post by LotsOfPhil on 2007-02-22
Hmm. To clarify, what do you want Firefox to do with jpegs?

---

### Post by phil54601 on 2007-03-02
I want the option to automatically download or any number of other things listed under the actions button.
Thanks 
Phil

---

### Post by LotsOfPhil on 2007-03-06
I'm stumped, sorry.

---

