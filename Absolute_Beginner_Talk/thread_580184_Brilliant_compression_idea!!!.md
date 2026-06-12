---
title: "Brilliant compression idea!!!"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-10-18
I have this idea, where instead of conventional methods of just compressing the data, it reads through it and looks up certain patterns.  I will read 1 MB at a time, and assign the pattern a number of 1 thought 1000 (I know there would be a lot more, I'm just using 1000 as an example ;)).  So, regardless of what the data is, or what format it's in, or how it's already compressed, [COLOR=DarkRed][B]every 1 MB would end up as just a few bytes!!!  Then, the decompresser would simply re-create the data using the number!

[/B][COLOR=Black]ex. 10010101101011101101011... equals, lets say, "29583".  the one MB would now be 5 bytes!  To decompress, it would convert the decimal number back to binary!!!
[/COLOR][/COLOR]

---

### Post by proalan on 2007-10-18
Your describing a LWZ compression method in your first sentance, something that is already used in compression utilities zip, rar, gz through pattern matching and use of dictionarys.

in Computer Science / Maths there is a threshold (max file size) for which something can be compressed. This represents the minimum amounts of binary digits required to store certain data otherwise known as the 'Entropy'. 

Multimedia files can't be compressed any further once they have been encoded. The compression / performance ratio of multimedia files are dependent on the algorithms used to encode them.

Compression is a very interesting subject that is overlooked by average users, its a integral part of all things related to computing including networking/multimedia.

---

### Post by ryanVickers on 2007-10-18
Well, what I'm thinking of, is yes, you take an mp3 and it will not compress, but it is, say, 4 MB.  What I'm thinking is it would read the first MB, assign the pattern a number, and then go on - you would end up with not actually a compressed version of the file, but more like a text document about 50 bytes in size read by the decompresser and then it would recreate the data patterns using the numbers.  ex of compression: "first MB" >> lets say, "28472".  second MB >> 28946, etc. ;)

It doesn't really compress the files, but more creates a tiny document saying what the files are...

---

### Post by petok on 2007-10-18
Then you would still need an enormous database for the decompressor to translate every 'number' to the corresponding pattern.

---

### Post by bobplano on 2007-10-18
that would be hard to make and would take a while, because you need a unique pattern for at least the different types of files, and some kind of algorithim to get what is specifically contained in the file. it would end up more than the bytes you say, but if it worked the file would be significantly smaller

---

### Post by ryanVickers on 2007-10-18
> **petok said:**
> Then you would still need an enormous database for the decompressor to translate every 'number' to the corresponding pattern.

I thought about that - storing every combo, but I concluded that that was pointless ;).  What it owuld do is convert the number into hex or decimal, and then store *that* number(s) as the file.  this would result in 1 MB being not compressed, but IU guess simplified to just a few bytes, no more than maybe 1 KB I think.  then the decompresser would convert the hex/decimal number back to binary!

---

### Post by Aikon- on 2007-10-19
What are the chances of you running into two blocks in a series of files with N total 1MB blocks that are the same?

In order for this compression scheme to gain any benefit, you would have to see the exact same sequence of 8,000,000 bits at least twice in any given block. This is because in order for the decompressor to be able to decompress the "encoded" bytes (i.e. the number that you have labelled the block with), you would have to send it an example of every block that appears. If there are no repeating blocks (i.e. each combination of 8,000,000 bits occurs only once [hint: this is a near certainty unless you are compressing two of the same file]), you would end up having to transfer the entire contents of the file(s) in uncompressed form.

What you are describing is very similar to trying to extract a file from a checksum. I thought about doing this once, as each checksum can be mapped to a list of combinations that match the reverse-crypto. You would have to process a **huge** solution space, and test each one against a logical test to determine whether it was valid or, before you would find the one that matches (what was probably) the original image.

Its akin to placing only a single letter in a book, and telling the reader to guess what the word is based on the context. If you have a sequence of these one-letter words, the error propagates as every missed-nuance when the reader selects a word changes the context under which the next one will be evaluated.

In short, I really don't think you're onto something here.

As proalan says, many compression schemes already use a similar idea, just with much smaller block sizes (thus drastically increasing the likelyhood of their repeating). I'm sure you could experiment with some of these tools by changing the block size, but for an arbirtrary input, I'm sure you'll find that the default values are optimized pretty well.

Aikon-

---

### Post by proalan on 2007-10-19
This post got me reading some of my old notes on this subject.

Heres a good (partial) summarized article on lossless compression.

 [http://www.cs.cf.ac.uk/Dave/Multimedia/node207.html](http://www.cs.cf.ac.uk/Dave/Multimedia/node207.html) 

There is also some controversy over LZW. Its the algorithm used for GIF that has been patented by compuserve. The PNG format was born as a result of this.

---

### Post by ryanVickers on 2007-10-19
I can see this isn't going anywhere - there must be some **huge** flaw that I'm not seeing, and/or everyone is too close-mined to see that it's brilliant! ;)

---

