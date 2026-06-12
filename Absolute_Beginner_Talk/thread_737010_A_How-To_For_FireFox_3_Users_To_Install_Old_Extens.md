---
title: "A How-To For FireFox 3 Users To Install Old Extensions"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-03-27
I've used this method since switching to Firefox 3/Swiftweasel 3  versions to install older versions of my favorite extensions, that won't normally install anymore.

1.) Find the extension you are interested in, and download it directly to your HD, instead of installing it thru the Addon manager in Firefox.  Instead of directly clicking on the Install button on the webpage, just right-click it, and select Save-As instead.

2.) Put that downloaded file into a directory of it's own.  Then unpack the .xpi file into the directory, using Archive Manager.  

3.) Edit the file named install.rdf .   Just use your normal text editor for this.  Look for the line of text that reads similar to this: <em:maxVersion>3.0b5</em:maxVersion>

The version number in the file will read different for each extension, but the main thing is to change that line of text to read like above.  This will tell Firefox that it's alright to install the extension as long as it's version number is 3.0b5 or below.

4.) Save your changes.  Delete the original .xpi extension file from the directory.  Open a terminal and cd into the directory you are in.  You now need to repack all those files and directories.

5.) First do a  ls  to get a list of all files and directories.  Next enter the command of :
   
zip -r filename.xpi <paste your list of files and directories here>

You can use any name you wish for filename.xpi .

6.)  That's it, you can now exit the terminal, and fire up Firefox.  Go to the Addons manager, and install the new custom extension.  

This has worked for me 99% of the time I've tried it, with aprox 10 extensions that weren't updated yet to work with Firefox 3 versions.  

Hope this will help some of you who want to use the new Firefox, but really don't want to do without the extensions you are used to.

FwFi

---

### Post by Wobedraggled on 2008-03-27
Slick, thanks for the info.

---

### Post by Austin_KW on 2008-03-27
Or disable compatability checking
Goto about:config
Right click and create a new boolean type "extensions.checkCompatibility" and set to false.

---

### Post by shuttleworthwannabe on 2008-03-27
or install the nightly tester tool; and in options disable the compatibility testing. 
NOTE: all of above methods may make FF unstable, hence not advised

---

### Post by FreewareFan on 2008-03-27
> **Austin_KW said:**
> Or disable compatability checking
Goto about:config
Right click and create a new boolean type "extensions.checkCompatibility" and set to false.

Well, that's certainly much easier than my method.  Wish I'd have known about it two days ago...  lol

---

