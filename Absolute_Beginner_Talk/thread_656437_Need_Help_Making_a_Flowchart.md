---
title: "Need Help Making a Flowchart"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by komputes on 2008-01-02
Hi everyone,

I'm trying to make a flowchart with graphviz, (but not the standart top-down type).

I have attached a picture and a few links of the flowchart I would like to make. If you guys know how to make one, please let me know. Thanks for your help.

[http://tinyurl.com/34eoyf](http://tinyurl.com/34eoyf)
[http://tinyurl.com/3b2p7d](http://tinyurl.com/3b2p7d)

---

### Post by nathandelane on 2008-01-02
So it looks like you're trying to make a state diagram using UML, right? What have you already done with graphviz?

Nathan

---

### Post by nathandelane on 2008-01-02
So I'm not going to say it can't be done, because that would be the antithesis of the Open Source community, but graphviz appears to be a graph making tool, more than a UML diagramming tool. Some other options you might try include Dia, which is a Linux open source diagramming tool, or OpenOffice.org Draw, which is a vector drawing tool. Another great vector drawing tool is Inkscape. Now I have used all three of these programs in the past for making diagrams, and I think it ultimatley boils down to what you want to use the diagram for, if you just want a graphic, then any of them will export to BMP, Tiff, PNG, or JPEG. If you want to include the digram in a document or presentation, then Draw objects incorporate well into other OpenOffice.org programs. If you're looking for quick and dirty, then Inkscape is my recommendation - it uses the SVG 1.0 standard. Dia doesn't have all of the possible UML diagramming symbols, but Draw and Inkscape don't have any of them. Both Draw and Inkscape do have lines that you can attach to objects like squares, circles, or spirals.

IMO, you should take a look at those while you are figuring out how to use graphviz.

Nathan

---

### Post by jrasmussen0 on 2008-01-02
I would use Inkscape which is a great vector graphics application.  It is not made to just do flowcharts but it is designed to create logos and non-photographic graphics.

In order to do this sample
1.  I started a new Inkscape document
2.  I imported the gif to the background and created a new layer for the design
3.  I created the circle and boxes with the correct fill and stroke (lines)
4.  I added the text and centered them in the boxes at the bottom
5.  I then created one arrow and duplicated for all the others
6.  I then added any text throughout the drawing
7.  Last, I had to place a white box without stroke/ lines behind text that crossed any lines to give it a nice white border.

---

### Post by Borbus on 2008-01-02
Yeah Inkscape rules. I once tried to use Visio because I heard good things about it but I soon became fed up and just did it in Inkscape quickly... Once you learn the keyboard shortcuts in Inkscape you can become extremely quick and efficient at using it.

---

### Post by komputes on 2008-01-03
> **nathandelane said:**
> So I'm not going to say it can't be done, because that would be the antithesis of the Open Source community, but graphviz appears to be a graph making tool, more than a UML diagramming tool. Some other options you might try include Dia, which is a Linux open source diagramming tool, or OpenOffice.org Draw, which is a vector drawing tool. Another great vector drawing tool is Inkscape.

Hey Nathan, I know how to use graphviz to make simple shapes/flowcharts I use inkscape as well (as well as other vector graphic tools) for all my design needs, but in this instance I would prefer to script this process in DOT language using Graphviz. Because in fact, the "quick n' dirty" solutions usually take more time than me typing it out. Anyone who's used Visio knows what I'm talking about. 

As for Dia and Office Draw, I'll give them a try. But I'd really rather script it...

By the way, thanks for letting me know that these are called "state diagrams". I was looking for the name for that particular type of chart.

And another one: [http://tinyurl.com/37mdfy](http://tinyurl.com/37mdfy)

---

### Post by nathandelane on 2008-01-03
Yeah as far as the scripting part goes, I know what you mean. Thanks for the reminder of what kind of diagrams those are, state diagrams, can't believe I forgot what they're called because I do a lot of them. Anyway I looked only as deep as the documentation for graphviz before I told you what I thought of it. It's main purpose is for creating graphs, as in discrete math's [graph theory]("http://en.wikipedia.org/wiki/Graph_theory"). I want to look deeper though, but I don't have an environment that will run graphviz available just yet. Have you tried yet to do anything with it? Here's what I think you might be able to do if you were to write a flowchart in the generic sense: You could probably write a script for graphviz that creates multiple smaller graphs, like one node, and link them together. I don't think it has any way of doing a state chart, at least not easily. You'll have to sort of "hack" a state chart out of it, and by that I mean try and use it for something that it wasn't meant to be used for. Dia is a true diagramming solution, but I'm still thoroughly confused by it (it doesn't exactly always produce the diagram I thought I made). So I usually use Draw - I mostly export my diagrams to PDF or MS Document format anyway (for everyone else), and if all I need is an image to pop into a document then I'll take the Inkscape route. Sadly there is still nothing that competes fully with Visio out there. Please keep posted if you figure out how to manipulate graphviz into helping you create a state diagram.

Good luck.

Nathan

---

### Post by nathandelane on 2008-01-03
Hey I just stumbled across something that would interest you - Kivio. And it's in the standard repositories for Ubuntu - in the package description it says it's a scriptable diagramming solution.  I've never used it before, but I'm installing it right now. It definitely should have state chart capabilities.

You should too.

Nathan

---

### Post by komputes on 2008-01-03
I like all these visio alternatives, they are very cool, but if anyone can help me with scripting this, it would be awesome.

---

