---
title: "Thunderbird Confusion"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by dln9 on 2008-02-09
I am running Gutsy Gibbon, and Thunderbird 2.0.0.6.  There are a few things I just cannot figure out.  

First, under "HELP", there is an option labeled, "Check for Updates...", but it is always greyed-out.  Why is that?  How can I make Thunderbird regain the ability to check for updates?  

I also have a problem with embedded images in Thunderbird emails.  I have "View>>Message Body As"  set to "Original HTML", and I have "View>>Display Attachments Inline" checked.  I am composing emails in HTML mode, and, I use the "Rich Text (HTML) Only" format when creating an email.  

I take a screenshot of my desktop, and save that screenshot as a jpg file.  Then, in Thunderbird, I create an email.  In the email, I click on "Insert>>Image".  I locate the jpg file and its location is entered into the box labeled "Image Location:".  "Attach this image to the message" is checked.  I select "Don't use alternate text".  Then, I click "OK", and I can see the image of the jpg file inline in the email I am composing just fine.  Then I send this email to myself.

When I open that email in Thunderbird, I cannot see the image inline in the email message.  Instead, it is in there as an attachment. 

(If I then right click on that message in the Inbox, and select "Edit as New...", I see a placeholder for the image, but not the image itself.)  

What must I do so that I can see images inline in emails I recieve? 

I did post this problem I just described for you on the Mozilla Thunderbird forum, but only one person responded with this after I sent him the message header information that apparantly showed that the MIME type that Thunderbird (?) assigned to this image was "application/octet-streams":  "The MIME type is totaly wrong for a JPEG image.  The valid type is image/jpeg or image/jpg.  The application/octet-streams is reserved for executable binaries such as  EXE, COM, SCR, etc.

If you were running MS Windows of any flavor the fix would be in it's registry.  I do not have a clue how Linux matches MIME types to file types, but that looks like the source of your problem."  

Since he didn't have a clue how to fix this problem in Linux, I thought I'd try this forum.  Does anyone know what I should do to fix this problem?  

My last problem is related (I think) to this image problem I just described.  When I receive an email from someone who uses Microsoft Outlook 11, and that email has an image file embedded in it - not as an attached file, but rather inline in the email - when I receive it in Thunderbird all I see in the email is this:  <-->  How do I fix this so I can see the image in the email when I recieve it in Thunderbird?   

Thanks in advance for any help.

---

### Post by Ewingo401 on 2008-02-09
Hi there, I'm still kind of new to Ubuntu too so I can't answer all of your questions.  However I can answer why the thunderbird update is greyed out.  In ubuntu all of the updates come from the update manager so when  a new thunderbird update is released it will be released as an ubuntu update.  You'll notice the same in firefox, its option to update is greyed out but it is also updated through the update manager.  Hope this helps.  Cheers!

---

### Post by LookTJ on 2008-02-09
Simple, you need to have root powers in order to use that. I recommend using the Update Manager(Synaptics) rather than bothering with that.

---

### Post by armitage1337 on 2008-02-09
Do NOT try to manually update Firefox or Thunderbird using the built-in updater by running as root. I did that once, and all my settings (addons, chrome, bookmarks) were lost. Allow Ubuntu to update Firefox automatically.

---

