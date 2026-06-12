---
title: "Latex - Picture indents too many lines"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by NanakiXIII on 2008-02-01
I'm using the picins package to insert images into a document I'm working on and they all work fine, except for one. For this one picture, the text besides it keeps being forced into a narrow column for about twice as many lines as are needed for the picture and its caption. I can't find any difference between the code I'm using for this picture and the code for the other pictures in the document. In fact, I tried just copying and pasting the code from another picture and changing the path and caption, but none if it has any effect. Has anyone ever seen this kind of behavior before?

---

### Post by eljalill on 2008-02-01
What kind of file are you trying to include? (Posting the commands in question might be most useful..)
Have you tried using graphicx anf floatingfigure instead?

---

### Post by NanakiXIII on 2008-02-01
This is the actual code I'm using.

```

\piccaption{De grafiek van $g(V t)$ laat zien hoe de drempel eruit ziet. \label{fig:graphDrempel}}
\parpic[r]{\includegraphics{graphDrempel.pdf}}

```

The picture is just a pdf image that I've created in the same way as I've created the other images in the document.

---

### Post by eljalill on 2008-02-01
I'm not sure, sounds odd...

 What happens to me sometime when I include pdfs is that the pdf is the shape of a whole page, with a picture in the middle. So whenla tex includes it, it includes all this white space, too... You could check whether this is the case here too... and use pdfcrop to get rid of the white space. 

Else you might just want to try, whether floatingfigure does the same strange thing... asf ar as I know you should be able to use both packages in the same document.

Oh, and you might find more help in the education&science subform, since it is mostly academics who use latex...

---

### Post by NanakiXIII on 2008-02-01
No, the PDF file really is just the picture. The caption is below the image and below that, that's where the white space is.

I'll try to use floatingfigure, but right now it seems my Latex distribution is unable to find the appropriate package on the server.

EDIT: I've managed to get rid of the whitespace by using \picskip to set the number of lines to indent manually. I'm still interested to know why  this problem is occurring, so if anyone knows, I'd still appreciate it if you let me know.

---

