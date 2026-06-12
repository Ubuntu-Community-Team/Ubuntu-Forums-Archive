---
title: "Graph Program"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by thedrizz on 2008-01-02
Heya,

I gotta put together a graph for an AP Chem lab report. What would be the best program to just throw in some data, set some parameters, and get a nice graph as a result?

---

### Post by dwhitney67 on 2008-01-03
Nothing is easy in life, including tying your shoes.  That's why velcro was invented.

If you want something where you can input numbers, draw a graph, sprinkle some salt over your shoulder, etc., then try Open Office (Spreadsheet).  It tries its best to be compatible with M$ Excel.

---

### Post by thedrizz on 2008-01-03
how would i do such?

---

### Post by dwhitney67 on 2008-01-03
Under the **Applications** pull-down menu, look for the **Office** sub-menu, then from there select **Spreadsheet**.

Once you launched the spreadsheet, you can select Help.

---

### Post by thedrizz on 2008-01-03
that is incredibly unhelpful. My attempts at using one column as a y axis and the other as an X is failing misreably

---

### Post by aktiwers on 2008-01-04
I know its a Windows app but I have used it with Wine many times.
[http://www.padowan.dk/graph/](http://www.padowan.dk/graph/)

Its very easy and runs perfectly with Wine.

---

### Post by thedrizz on 2008-01-04
sudo wine (path to exe) doesn't work. Whats the correct method for install?

---

### Post by dwhitney67 on 2008-01-04
> **thedrizz said:**
> that is incredibly unhelpful. My attempts at using one column as a y axis and the other as an X is failing misreably

Below are some basic instructions (by the way, this is the first time I did this too!).  I figured most of it out by experimentation and deductive reasoning.

See the attachment for an example spreadsheet with a graph.  Unfortunately I couldn't post an .xls file, so I had to resort to including a tar file.  To un-tar, follow these instructions:

1.  Save the tar file (Pie.tar) to disk
2.  Goto the directory where you saved the tar file.
3.  tar xvf Pie.tar

```
Launch Spreadsheet application.

Enter data in a column.
Enter identifier for data in separate column.

Add Chart...

Select Chart type
Click on Next

Enter Data Range (e.g. B1:B6)
Select Data Series in Columns
Select First Row as Label
Unselect First Column as Label
Click on Next

For Categories, enter data range (e.g. A2:A6)
Click on Next

Enter a 'Title' and 'Subtitle' (if required) for the graph
Click on Finish.
```

---

### Post by Paqman on 2008-01-04
[Google Docs](http://docs.google.com/) has a nice simple spreadsheet ap.

---

### Post by twin_57103 on 2008-01-04
When is the report due?

Would you give some more specifics about what you're trying to graph?  I have a bachelor's in chemistry, but it's hard to know what you're trying to do.  What kind of data do you have and what kind of graph do you want?

Sometimes spreadsheet programs require a couple tricks.  Try searching the web for an Excel solution.  Chances are you'll be able to do it in Open Office.

---

### Post by thedrizz on 2008-01-04
oh, i dual booted to windows and used that program aktiwers linked too, it worked like a charm. Thanks for all the help.

I'm trying to graph the relation between the &#955; nm and the % transmitted from a permagnate solution, and the observed absorbance.

I am not so hot at this.

---

### Post by twin_57103 on 2008-01-04
Glad to hear you got it to work.  From your description, this was essentially a scatter plot (a line graph is a scatter plot where the dots are connected, possiblly with smoothing).

I've used Excel more frequently than Open Office Spreadsheet since that is what I've got available at work.  In Excel, the trick for this kind of plot is that the "chart wizard" usually does not place the X and Y data in the right place.  You can generate the chart, then edit it to select one as the series and the other as the range.  I haven't tried this in Open Office, but it might be similar.

You will do yourself a favor if you get the hang of spreadsheet software now, before you get into college.  Regardless of your career goals - business, science, or other - you will need to produce charts & graphs for college and later for work.

There are a lot of good Excel tutorials available online, and I'd imagine there are a few directly for Open Office.  Most things in Open Office are similar to Excel, although they may be in a different place.

Best wishes,
twin_57103

---

### Post by aktiwers on 2008-01-04
I just set all exe files to open in Wine. Right click on an exe file, pick properties, pick "open with" tab and pick Wine.

Hit "OK" and then just double-click the exe :)

---

