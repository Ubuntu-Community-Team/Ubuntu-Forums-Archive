---
title: "Firefox downloads"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by someusernoob on 2006-06-14
Little anoying problem:

I accidently checked the box 'Do this for files automatically from now on' when i wanted to download a tar.gz file.

My preference in the Downloads section under Edit was to save every file to a specific folder, but it always still used to ask if i would open the file, or just save it. Now it saves those tar.gz files automaticly. Aargh. (When i try to download an .iso it just asks me what to do with it, thats how it should be)

In this same Downloads section there is a button with View & Edit Actions, but the tar.gz file isnt between the other files (only some media stuff like quicktime). So i'm not able to restore my old situation.

Deleting my .firefox folder to reset all settings isnt an option since configuring my extensions takes sooo much time. and i couldnt find a file in there with the setting im looking for.

Can someone help me out on this one?

---

### Post by u.b.u.n.t.u on 2006-06-14
Type "about:config" in the address bar.

Look for "browser.download" etc. I have had a look to see which option it might be but I am unsure.

Also maybe:

Edit > Preferences > Downloads 

Anything in the "Download Actions", "View & Edit Actions" ?

---

### Post by someusernoob on 2006-06-14
Can't find anything usefull in about:config actually.

And as i mentioned in my first post, the weird thing is that it isn't in View & Edit Actions, only some media files like quicktime etc. Nothing about a .tar or any other archive thing.

Thanks for helping anyway :D

---

### Post by u.b.u.n.t.u on 2006-06-14
This is from the help file. I thought it best to just paste it here.  Also try "Save all files to this folder". Close Firefox, then open Firefox, then change it to "Ask me where to save every file". Maybe that will do it. It is a tricky problem.


```
Download Actions

    
The Download Actions dialog, which can be opened by clicking the View
      & Edit Actions... button, contains file types that you have
      downloaded. You can choose what Firefox should do when clicking
      on a specific file type by selecting the file type you want to modify and
      clicking the Change Action... button.


This will display the Change Action dialog, where you can choose to have
      the file type opened by the default application, opened by a user-selected
      application, saved to disk, or shown with an installed plugin. For
      example, if you view lots of media files on web pages, you might want to
      specify that Firefox always open media files in your media player
      instead of asking where you want each media file to be saved.


    *       Open them with the default application:

              Select this optionpreference to open this file type in the default
              application for that file type (determined by the operating system).

    *       Open them with this application:

              Select this optionpreference to specify another application that should
              handle this file type. You will see a dialog asking you to specify the
              application to use.

    *       Save them on my computer:

              This optionpreference will save the files to disk. If you have the
              Save all files to this folder optionpreference enabled, the files
              will be saved automatically.

    *       Use this Plugin:

              Select this optionpreference to let a plugin handle this file type.


To remove an automatic rule for a file type, select that file type in the
      Download Actions dialog and click the Remove Action button.


```

---

### Post by someusernoob on 2006-06-14
Found another way to fix it:

In the home/*/.mozilla/firefox/somename/ folder is a file named mimeTypes.rdf. In it was some data about how to handle different types of archives when downloading, but nothing specific about tar.gz. So after al little playing around with the True False options i decided to just remove the file from this directory. and it seems that i worked out very well.

And yea, i should've checked out the help file, lol, i have so many "bad" experiences with them, i dont even think about m anymore. Thanks for the input. Thats what makes this community so wonderfull!! :D

---

