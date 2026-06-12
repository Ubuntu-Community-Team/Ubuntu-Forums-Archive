---
title: "DVD / Music / Book Catalog"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by aflatun on 2006-02-05
Is there a simple program I can use to catalog my books and DVDs linux? I would like something I can install from Synaptic because I still haven't figure out how to download and make apps. One step at a time right?

I would also like to eventually post my catalog on the web, any suggestions? In windows, I just used Excel and had a script produce formatted xml files which I then posted the web. I know I can still do that but I wanted to explore to see if there was something neater. (No I am not yet confident enough to try active database online, it will be static for now.)

---

### Post by Praetorian on 2006-02-06
I can't find a app thats catalog you books and dvd but for your book you can use Alexandria and for you DVD's you can use ceemedia 
To install Alexandria:
```
sudo apt-get install Alexandria
```
To install ceemedia:
Download the .deb file [here ]("http://prdownloads.sourceforge.net/ceemedia/ceemedia_0.5.2.1.deb?download")
```
sudo dpkg -i ceemdia_0.5.2.1.deb
```

---

### Post by MadL on 2006-02-06
Thanks, Praetorian! I've been looking for a book cataloging program too, and Alexandria looks like it just might do the trick.

---

### Post by aflatun on 2006-02-07
Praetorian, thank you very much for your answer. Alexandria is a great program for a book catalog. It is so cool that it can export data as html which I can just post to my website.

For the DVD organized I chose to go with gcfilms since its available from synaptic and seems to work great.

---

### Post by blair on 2006-02-07
You could of course also use OpenOffice Calc (MS Excel clone) or Base (MS Access clone). Both free and included in Ubuntu. You just have to create your own tables, column headers, etc. You can customize it to your heart's content.

---

### Post by Bone Down on 2006-02-07
[QUOTE=blair]You could of course also use OpenOffice Calc (MS Excel clone) or Base (MS Access clone). Both free and included in Ubuntu. You just have to create your own tables, column headers, etc. You can customize it to your heart's content.[/QUOTE]

quick question can OO. Base open and utilize *.mdb files??
I have a friend that wants to share his catalog with me, but he is stuck in windows and will hear nothing of using linux.

---

### Post by graabein on 2006-02-14
[QUOTE=Bone Down]quick question can OO. Base open and utilize *.mdb files??
I have a friend that wants to share his catalog with me, but he is stuck in windows and will hear nothing of using linux.[/QUOTE]

I have not tried Oo Base myself but you can always try to export the data to a common format from Access or maybe go via Excel and then save as *.csv?

A pity I never got Alexandria to work... When I do a search I never get any results. What are you guys doing to add books to the library? Even if I do a simple "Bukowski" search on any of the sources I get nothing... It says on the website that books can be added by hand... Guess I have to resort to this...

:-k

---

### Post by MadL on 2006-02-14
[QUOTE=graabein]A pity I never got Alexandria to work... When I do a search I never get any results. What are you guys doing to add books to the library? Even if I do a simple "Bukowski" search on any of the sources I get nothing... It says on the website that books can be added by hand... Guess I have to resort to this...
:-k[/QUOTE]

Hmm. I usually click the "Add Book" button and search by ISBN. Does it seem as if Alexandria's trying to search and not returning any results, or is it not even trying?

---

### Post by graabein on 2006-02-15
Well I finally got it working. I had to uncomment two require-lines in **/usr/local/lib/site_ruby/1.8/alexandria/book_providers/z3950.rb** before Alexandria would load and the search works just fine. I punch the ISBN-code and the right book pops up. Excellent.

Edit: Except for Norwegian books that is...




BTW: I tried Oo Base and on the start-up wizard there's an option for *connect to existing database* and I saw Microsoft Access in the pulldown menu. Try it out Bone_Down!

---

### Post by A-star on 2006-04-07
any other suggestion for a good book catalog for linux?
I want to automatically add dutch books.

---

### Post by quini on 2006-05-12
[QUOTE=A-star]any other suggestion for a good book catalog for linux?
I want to automatically add dutch books.[/QUOTE]

I'm also interested in finding another book managing software for linux; Alexandria seems fine, but it hangs very often in my box  :???:

---

### Post by royg1234 on 2006-07-05
I've been looking at web-based.  [www.listal.com](www.listal.com) is in beta, but looks really good.  or for a DIY, look at VCD-db [http://vcddb.konni.com/](http://vcddb.konni.com/) (this one also needs some work).

---

### Post by Thundercat on 2006-07-05
I found alexandria on a download site. It says it is a Gnome application. Will it run under Kubuntu? 
Specifically I am going to be running Kubuntu AMD64 build...

---

### Post by Blues- on 2006-07-18
> **royg1234 said:**
> I've been looking at web-based.  [www.listal.com](www.listal.com) is in beta, but looks really good.  or for a DIY, look at VCD-db [http://vcddb.konni.com/](http://vcddb.konni.com/) (this one also needs some work).

Hi, since I'm the author of VCD-db, i want to say it's fun seeing it mentioned here, but I´d like to hear your comments on what more features/work you want to see done additionally on VCD-db.

Cheers,
Konni.

---

### Post by gurgle on 2006-07-21
is there a .deb of VCD-db available?

---

### Post by Blues- on 2006-07-21
> **gurgle said:**
> is there a .deb of VCD-db available?

Unfortunately no, but i think I'll take a closer look howto create deb files, VCD-db comes with it's own installer so you should be able to have VCD-db up and running in under a minute.

You can d/l the latest release at the [VCD-db website]("http://vcddb.konni.com/?v=9").

Cheers,
Konni.

---

### Post by gurgle on 2006-08-01
GCStar is out, from the maker(s) of GCFilms

[http://www.gcstar.org/index.en.php](http://www.gcstar.org/index.en.php)

---

### Post by gurgle on 2006-08-08
> **Blues- said:**
> Unfortunately no, but i think I'll take a closer look howto create deb files, VCD-db comes with it's own installer so you should be able to have VCD-db up and running in under a minute.

You can d/l the latest release at the [VCD-db website]("http://vcddb.konni.com/?v=9").

Cheers,
Konni.

is there another database like this that i can include my music collection in as well. also, the site is down for me.

---

### Post by parys on 2006-08-09
> **Thundercat said:**
> I found alexandria on a download site. It says it is a Gnome application. Will it run under Kubuntu? 
Specifically I am going to be running Kubuntu AMD64 build...

I'm going to blow my own horn here and suggest you try Tellico, which I wrote. It can handle books, dvds, music, and several other collection types. It's a KDE app. [http://periapsis.org/tellico/](http://periapsis.org/tellico/)

I believe it's in the multiverse repo, though I'm not sure since I don't use Ubuntu. Try searching for it in synaptic.

---

### Post by keith whitehouse on 2006-08-16
hi parrys,

I run a gnome desktop and to my knowledge I have no kde programs installed?. Will Tellico run in gnome please.

best regards keith

---

### Post by quini on 2006-08-16
> **keith whitehouse said:**
> hi parrys,

I run a gnome desktop and to my knowledge I have no kde programs installed?. Will Tellico run in gnome please.

best regards keith

Of course; maybe the fonts and appearance are not going to be that nice, but that's all  ;)

---

### Post by eeried on 2007-02-26
Tellico looks very nice but can you add book providers easily. I'd like to use Tellico or Alexandria to make the catalog of a small publlic library (3000 books approximately) and all are french or in French.

I've found some help as how to make the Amazon.fr work, and  with the accented letters(it doesn't without a workaround -- here's the link for those interested [http://forum.ubuntu-fr.org/viewtopic.php?id=35140]("http://forum.ubuntu-fr.org/viewtopic.php?id=35140")

Tellico is probably better if only because it actively developed. However the Dapper package seem to be very old...

Tellico might be installed on the latest Knoppix Live-CD (5.1.1:(just astounding version!).

---

### Post by rmdeal on 2007-10-14
alexandria is wonderful!.  I've worked in several small libraries and done a bit of cataloging there.  I find looking for mark record-type data from Alexandria much easier than using the conventional Library of Congress route.  I have a large library of books of various sorts at my home and look forward to organizing my alexandria libraries after adding a few more books.

At first I was frustrated in that some books were either not recognized at all or rejected because of some field not being complete.  I'll have to check into the latter - has anyone else had this problem?  However, after looking a bit closer at the help documentation, I learned how to manually enter a book.  It is neat to have so many of the books entered showing up in the icon view with the actual book cover.

---

### Post by michaelzap on 2007-10-14
> **gurgle said:**
> GCStar is out, from the maker(s) of GCFilms

[http://www.gcstar.org/index.en.php](http://www.gcstar.org/index.en.php)

GCStar is way nicer than GCFilms was! I'm gonna start using it instead of Movie Collector via Wine. Thanks for the heads up!

---

### Post by milesje on 2008-03-27
This thread is a little old but I thought I would put my say in. I use Data Crow ([http://datacrow.net](http://datacrow.net)). It is a java application and allows you to do collections of just about everything and can use the web to search and add items easily.

---

