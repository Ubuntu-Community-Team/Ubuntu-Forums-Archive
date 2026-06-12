---
title: "Signatures and stationery in Evolution"
date: 2006-08-21
forum: Art &amp; Design
---

### Post by rockx00 on 2006-08-21
[B]I was just curious to know if someone out there knows how to make the executable scripts for importing into the signature area of Evolution?  With outlook, all you did was add HTML code to your HTML editor and it pretty much too care of itself after that.  I tried opening a standard text file and then importing it into Evolution, but it said that it had to executable.  I am just looking to make holiday emails and such and maybe put a clickable link to my homepage in my standard signature and maybe format the backgrounds of each of my emails that I compose.

Also if anyone knows of a stationery file that can be downloaded for Evolution, please pass that information along as well.  

Any information that anyone can provide is highly appreciated.

Thanks,

Brian[/B]

---

### Post by hughh on 2007-09-01
> **rockx00 said:**
> **... curious to know if someone out there knows how to make the executable scripts for importing into the signature area of Evolution**?

Yes, I just figured this out.  The only stumbling block I ran into is that the script has to produce an HTML signature; text signatures are interpreted as HTML.

I wrote a bash script for each signature I wanted. Writing a bash script means creating a text file with bash commands in it (I hope I'm not insulting your intelligence :)). 
Here's a simple one:

```
echo "--<br />Hello World!"
```The file containing this command must be made executable from a terminal command line:

```
chmod +x <script name>
```If you then link your script from Evolution to this file, when you invoke the script it should add the following to the end of your [empty] message:

> --
Hello World!Mine actually look like sorta like this:

```
 perl ~/bin/SetSig.pl ~/TagLines.txt ~/.evolution/signatures/signature-1 2>&1 >/dev/null \
| cat ~/.evolution/signatures/signature-1 \
| sed 's/[        ]+$/$/' \
| sed 's/ /\&nbsp;/g' \
| sed 's/$/<br \/>/'
```It uses a Perl script called SetSig.pl that I wrote years ago to take randomly select a quotation from the file ~/Taglines.txt (I've collected over 6,000 of them so far) and replace the existing quote at the end of a predefined signature.  In Evolution, I created a plain text non-scripted signature with a quote at the bottom, then snooped around for where Evolution keeps its signature files: ~/.evolution/signatures/signature-<n> (where <n> is a sequential integer beginning with 0).  The Perl script replaces whatever quotation is at the end of this signature file (defined as whatever follows the last two consecutive NLs in the file) with the new randomly selected quotation.

That gets us up to the cat command.  Evolution scripts require the signature to be on stdout.  cat simply copies the contents of the file to stdout.


The three remaining sed commands do the following respectively.[LIST=1]
[*]Delete trailing whitespace [<space>,<tab>] from each line.  I do this just because I'm meticulous and ornery. ;)
[*]Replace every <space> with an HTML non-breaking space (HTML interpreters will reduce multiple whitespace characters to a single space).  This is probably overkill, but it was the quickest and simplest way to get the job done.  This has to follow the first sed command or else there's no trailing whitespace to get rid of.
[*]Put an HTML break (<br />) at the end of each line.  This sed command has to follow the second so I don't get "<br&nbsp;/>, which is not valid HTML.[/LIST]Here's an example of the output from my script:

```
--&nbsp;<br />
Hugh&nbsp;D.&nbsp;Hyatt<br />
Legend&nbsp;Consulting&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;e-mail:&nbsp;hugh.hyatt@legend-consulting.com<br />
611&nbsp;Dale&nbsp;Road&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;web:&nbsp;http://legend-consulting.com<br />
P.O.&nbsp;Box&nbsp;143&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;voice:&nbsp;+1.215.947.1799<br />
Bryn&nbsp;Athyn,&nbsp;PA&nbsp;19009&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fax:&nbsp;+1.603.316.0347<br />
<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Eyes&nbsp;that&nbsp;do&nbsp;not&nbsp;cry,&nbsp;do&nbsp;not&nbsp;see.<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;--&nbsp;Swedish&nbsp;proverb<br />
<br />
```After Evolution gets this and processes it, it comes out thusly:

```
    -- 
    Hugh D. Hyatt
    Legend Consulting                   e-mail: [EMAIL="hugh.hyatt@legend-consulting.com"]hugh.hyatt@legend-consulting.com[/EMAIL]
    611 Dale Road                                web: [http://legend-consulting.com]("http://legend-consulting.com/")
    P.O. Box 143                                      voice: +1.215.947.1799
    Bryn Athyn, PA 19009                                fax: +1.603.316.0347

                      Eyes that do not cry, do not see.
                                     -- Swedish proverb
```I hope this is of some help to you.

---

