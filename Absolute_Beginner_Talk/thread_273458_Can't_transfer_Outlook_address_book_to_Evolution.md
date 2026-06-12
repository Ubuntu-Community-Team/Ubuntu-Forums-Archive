---
title: "Can't transfer Outlook address book to Evolution"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2006-10-08
As the title suggests.

I've followed this How to , by importing from OE to Thunderbird in Windows [http://www.ubuntuforums.org/showthread.php?t=91687&highlight=Import+Outlook+to+Evolution](http://www.ubuntuforums.org/showthread.php?t=91687&highlight=Import+Outlook+to+Evolution)

but I don't seem to get the "file with no extension".  There is nothing there relating to address book.

This is quite an old Howto so I wonder if somebody has another idea?

Thanks

---

### Post by Phosphoric on 2006-10-09
Seems a shame if nobody can help with this.  This is my last hurdle to moving my wife over to Ubuntu.  If I can't migrate her Outlook Express stuff to Ubuntu then it's dead in the water.

Thanks.

---

### Post by Roger Mudd on 2006-10-09
Try exporting your Outlook Express address book to a comma seperated file. Then import that file into Evolution. This method worked for me with Outlook. I would imagine that it will work with OE as well.

---

### Post by Phosphoric on 2006-10-09
Roger, could you expand on "comma seperated file" please?

Thanks.

---

### Post by TheMono on 2006-10-09
Often referred to in Outlook as CSV I think, comma seperated values.

It's basically a text file with all the different fields seperated by commas.

---

### Post by Phosphoric on 2006-10-09
Thanks folks,

I'll give it a try when I get home from work.

Cheers. :)

---

### Post by Roger Mudd on 2006-10-09
Yes, what TheMono said. Sorry for the confusion. Here's how I would go about exporting the CSV from OE:
1) Open Address Book (Start>All Programs>Accessories>Address Book  or do so from within OE)
2) File>Export>Other Address Book...
3) Select Text File (Comma Seperated Values) from the next dialog.
That should prompt you to save the CSV file somewhere. Then log into Ubuntu and import that file into Evolution. I've included some screenshots below to help you along.

---

### Post by Phosphoric on 2006-10-09
Well, I've followed the instructions so far and did indeed get a CSV file which I saved away.  

In to Evolution and Import.  This time it recognised the file type, gave me an option of Evolution, Mozilla or Outlook Express.  Chose OE and clicked forward.  A small activity and then off to find my address book....no good.  Went back and tried importing as one of the other types of file, still no evidence of my address book in Evolution.  Had another look at the saved file and my data is all there as expected.

Evolution dosen't seem to like me....neither does Ubuntu to that matter:( , everything seems to be such a struggle.

Any more thoughts folks?

Thanks

---

### Post by Roger Mudd on 2006-10-09
I had something like this happen when importing an Outlook 2003 address book in CSV format. After it failed to populate the address book the first time I tried it again immediately (without restarting Evolution) and it worked. Strange, but it did work for me.

---

### Post by hartdg on 2007-08-12
> **Phosphoric said:**
> Well, I've followed the instructions so far and did indeed get a CSV file which I saved away.  

In to Evolution and Import.  This time it recognised the file type, gave me an option of Evolution, Mozilla or Outlook Express.  Chose OE and clicked forward.  A small activity and then off to find my address book....no good.  Went back and tried importing as one of the other types of file, still no evidence of my address book in Evolution.  Had another look at the saved file and my data is all there as expected.

Evolution dosen't seem to like me....neither does Ubuntu to that matter:( , everything seems to be such a struggle.

Any more thoughts folks?

Thanks

I was successful (moving contacts from MS-Outlook, not Outlook Express) selecting "TAB delimited (Windows)" file format. 

Evolution (ver 2.10.1) took it like a charm (even a file with 23000 contacts in it). 

My first attempt was with a "comma separated file" format but the "mapping" proposed by Outlook resulted in the data being scrambled in Evolution.

I have found some things a struggle, and for me, that's part of a challenge that I enjoy. I am finding that with time (and research in forums like this) things become easier.

Dave

---

### Post by tashmooclam on 2007-08-12
I haven't done it, but one could upload the outlook address book to gmail. It's a start. 
[http://mail.google.com/support/bin/answer.py?answer=8301](http://mail.google.com/support/bin/answer.py?answer=8301)

Then, maybe you can then export this same address book to evolution or thunderbird. 

[http://mail.google.com/support/bin/answer.py?answer=24911](http://mail.google.com/support/bin/answer.py?answer=24911)

This may be unduly clunky, complicated, Flinstone for a reasonable person to try. I get a headache just reading it almost. 
But, you never know, it could work.
I hardly use my thunderbird anymore, they send me so much junk it's almost useless anyway. I am mostly using gmail now.

---

