---
title: "text editing"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by MNR25 on 2007-04-23
Hi

(if this is posted in the wrong place - my apologies!)

I am using ubuntu (7.04) for text editing related programming at the moment. (all the tr/grep/sed stuff you can dream about - it's like text-magic!) Thing is, the source material is all OCR generated and due to that being done in a Windows environment every single line has some stupid hidden character added (forgot the name for it but hexadecimal is 0A) but basically it stops any command trying to work with end-of-line stuff.

So I have a heap of files ready for analysis, but the final steps have to wait until I remove said character using a hex-editor. Since this involves a few dozen files I want to automate part of the process. Is there a way to do this?

1) sed -e '/^/@/g' < example.txt > example.H.txt
2) remove hexadecimal 0A using hex-editor (ghex), save as example.H.txt
3) sed -e '/@/\n/g' < example H.txt | sed '/^$/d' > example.txt

What I like to accomplish is a way in which I can say "apply 1) to the following files: file1, file2...fileN and save each file (under the same, or a different filename)

Then after hex-editing I like to do the same for 3)

I used to be able to write stuff like this in awk but I forgot how and for some reason it just won't come back to me, my brain is getting too old. Unless it involves rather complicated programming I'd really like to know more about this!

---

### Post by finer recliner on 2007-04-23
0x0A is the ASCII new line character. windows obviously has conflicting methods of intrepting a newline character (some software only uses carraige return, some use only new line feed, some require both chars).

you can write a simple bash shell script to help you delete the new line chars. if that doesnt work as expected, try replacing them with a carriage return char. a perl script would also work, as it is also good for manipulating text.

more ASCII refrence: [http://asciitable.com/](http://asciitable.com/)

---

