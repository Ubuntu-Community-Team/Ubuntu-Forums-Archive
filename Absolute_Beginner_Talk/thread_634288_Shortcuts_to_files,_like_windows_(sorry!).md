---
title: "Shortcuts to files, like windows (sorry!)"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by sipickles on 2007-12-07
Hi,

I am struggling getting links to files to work. They seem counter intuitive.

I want to create a link in a folder which opens a file in a subfolder. I want it to act as if I had clicked the LINKED TO file, not the LINK, which is what it is doing. ???

To elaborate, doxygen generates a folder called html with hundreds of files in. I want to make a link to the index.html so I don't have to trawl the folder each time.

I want a:

    docs/link_to_index

to run:

    docs/html/index.html

It runs it but files linked relatively to index.html are missing (since it is running as if in docs folder, not docs/html)

This is most bizarre behaviour.

Is a link not a link but a copy???

Thanks for your help

Si

---

### Post by chris_nava on 2007-12-07
The issue here is that the index.html file's links are incorrect relative to the location of the file (link).
Unfortunately, (for you) the browser does not change its perspective when accessing files through a link.
Note that this is NOT a bug.. the intended function of links in *nix file systems that the application access the link's destination as though the file it were in the linked location.

To solve your issue you'll need to perform one of the following:
A. Copy the index.html file into the new location and fix the html links inside to point to the correct folder.
B. Create a new index.html file in the new location that contains a meta-redirect tag that links to the version in the subfolder.

Both options use HTML not the file system to produce the desired result.

---

### Post by Crashmaxx on 2007-12-07
I see the problem you're having, and I'm not sure quite why it works that way. But I know a solution.

Go to your desktop and right click, select "Create Application Launcher", set the type to "Location" and give it a name, and then type in the path to the file you want or select it with browse. Click OK and move it where you want the shortcut to reside.

Hope that works for you!

---

### Post by smartboyathome on 2007-12-07
Links in Linux use the file path of the link. So if I had (for example) a folder located at /home/user1/foo, and wanted to symlink it to /home/user2/foo, I could do that by making a link. The folder would be treated as an actual path, though, so if there was a file in it called file in /home/user1/foo, and user2 opened it in their home directory, then it would be treated as if it were in /home/user2/foo.

---

### Post by sipickles on 2007-12-07
Thanks crashmaxx. this round-a-bout way actually works.

Its stupid and a pain in the rear that it is required. 

I thought Ubuntu was all about customisation.... I'd like to see more flexibility in the releases, rather than me having to rebuild the kernel with my own modifications etc etc

---

