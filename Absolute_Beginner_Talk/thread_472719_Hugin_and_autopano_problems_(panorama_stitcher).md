---
title: "Hugin and autopano problems (panorama stitcher)"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by adamklempner on 2007-06-13
I am trying to use Hugin to create a panorama in Kubuntu 7.04.  I have installed Hugin and autopano-sfit (control point generation program) from the repository.  When I have used these programs in the past on Linspire the process was generally:  1) import pics 2) generate control points 3) stitch.  However, in Kubuntu, when I click on "Create control points" I get the following error in a window called "wxExecute Error":

> command: autopanog.exe --output autopano_result_tempfile.pto --imagelist /tmp/ap_imgnamesXaqgFN
failed with error code: 127

and when I run Hugin from the konsole this error is what is shown at the prompt when attempting to generate the control points:

> sh: autopanog.exe: not found

It is strange that it is trying to call an exe.  How can I make Hugin interact with autopano correctly?

---

### Post by kevinlyfellow on 2007-06-15
Looks like a cool program, so I installed it and I get the same error you do.  I'm going to try the debian ports, and see if its an ubuntu specific problem.

Update:  Well, its not going to be easy installing a debian version...

---

### Post by _bert_ on 2007-06-15
Hi there,

there's sort of a short Howto in German at the German Ubuntu forums:

<http://forum.ubuntuusers.de/topic/89523/>

In very, very brief:
You may first install autopano-sift from the repos...

Goto "File/Preferences/Autopano"
Check the "Use alterantive Autopano-SIFT-Program"
Use "autopano-complete" instead of autopano.exe or autopanog.exe, and pass the arguments "-o %o %i" instead of "--output %o --imagelist %namefile ". 
open autopano-complete.sh in your favorite editor and adjust the path...
This should do it.



HTH,
Bert.

---

### Post by kevinlyfellow on 2007-06-15
Actually, I couldn't find autopano-complete.sh 

Instead, what I did was instead of using autopanog.exe I used autopanog.  Pretty simple!

---

