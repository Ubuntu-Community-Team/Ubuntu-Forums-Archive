---
title: "Java program in firefox (.jar) wants to download and not run."
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Gen2ly on 2007-04-15
I wanted to run the Video Uploader for Google Video [here]("https://www.google.com/video/upload/UploadInfo?hl=en").  But when I click the link it tries to save a .jar file.  I think it supposed to run something.  Is there something I need to do to Firefox to make this run?

---

### Post by RomeReactor on 2007-04-15
Hi. In Firefox, go to "Edit-->Preferences-->Content" and make sure **Enable JavaScript** and **Enable Java** are both checked; then i suggest you go [here]("http://www.java.com/en/download/help/testvm.xml") to see if it's running fine. As for the .jar file, since I couldn't open the page you linked, I can't really say. Maybe you *do* need to download the file and run it afterwads (perhaps by double-clicking on it).

---

### Post by Gen2ly on 2007-04-15
> **RomeReactor said:**
> Hi. In Firefox, go to "Edit-->Preferences-->Content" and make sure **Enable JavaScript** and **Enable Java** are both checked; then i suggest you go [here]("http://www.java.com/en/download/help/testvm.xml") to see if it's running fine. As for the .jar file, since I couldn't open the page you linked, I can't really say. Maybe you *do* need to download the file and run it afterwads (perhaps by double-clicking on it).

RomeReactor, I appreciate the help.  Both java and javascript are enabled in Edit > Preferences > Content.  Its possible Firefox for some reason isn't dectecting it as an executable, and trying to download it.   If I download it and double click on it File-roler opens up.

Here's a screen if it helps.

---

### Post by RomeReactor on 2007-04-16
Have you tried right-clicking on the .jar file to open it with Firefox? I seem to recall there are a few browser-based games that require you to download a .jar file and execute it so, though I'm not sure at the moment. Sorry.

---

### Post by RomeReactor on 2007-04-16
I just remembered I had a Google account, so I went through the steps to use the Video Uploader: Turns out you **do** have to download the .jar file. In [this page]("http://video.google.com/support/bin/answer.py?answer=31701&ctx=sibling#downloadinglinux") it says to open a terminal and enter

```
java -cp Desktop/GoogleVideoUploader.jar com.google.uploader.Uploader
```

where **java -cp Desktop/GoogleVideoUploader.jar** is the path to the .jar file you downloaded; that will bring up the program.

---

### Post by Gen2ly on 2007-04-16
> **RomeReactor said:**
> I just remembered I had a Google account, so I went through the steps to use the Video Uploader: Turns out you **do** have to download the .jar file. In [this page]("http://video.google.com/support/bin/answer.py?answer=31701&ctx=sibling#downloadinglinux") it says to open a terminal and enter

```
java -cp Desktop/GoogleVideoUploader.jar com.google.uploader.Uploader
```

where **java -cp Desktop/GoogleVideoUploader.jar** is the path to the .jar file you downloaded; that will bring up the program.

RomeReactor, very very glad you located that thanks!  Did the trick for me.  Why it wasn't in the first page of instruction I have no idea.

:D

---

