---
title: "Change Multiple Lines in Multiple Files in Multiple Subdirectories"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by OmahaVike on 2007-03-21
hello,

i'm finding myself in a new place here, and am hoping someone can help me with this situation:  i need to change multiple lines in multiple files within multiple subdirectories.

i have several subdirectories of .cfm files (please don't ask why), which need certain elements inside of them changed:

existing code inside of the files:
```

<!--    <cfset sName=ReplaceNoCase(Replace("Ubuntu Forums Rock","&nbsp;"," ", "ALL"),"<br>","","ALL")>
    <cfif "po" EQ sFullNav>
        <cfset sBreadcrumb = sBreadcrumb & "<span class=""textpink"">"  "</span>">
    </cfif>--><div id="ap" class="button" >

```

see where i've commented out the part i want to erase?  i only want the files to be left with the div tag:

```

<div id="ap" class="button" >

```

the "gotcha" is that these are multiple lines, and not a single line.  furthermore the string "Ubuntu Forums Rock" could, and are, variable and can change from file to file with no set length.  i do believe everything else is rock solid static throughout all of the files.

another "gotcha" is that i've used the html comment tag only for this example, so that cannot be relied upon for parsing.  i only added it as a visual reference for the part i need to remove.

i'd love to be able to do this without a shell script, so any and all help from a CLI perspective would be great.  pure guess is that it'd start out with a find command and then piped into some type of perl command.

thanks once more for any/all replies.

---

### Post by tomchuk on 2007-03-22
Would it be possible to attach a couple of the files. I'm pretty sure I can work out some sed magic to do what you need, but I need a clearer picture of what the source files look like.

**NOTE** drop the -i argument to sed in the following examples for the changes to be printed to stdout as opposed to changing the files.

For something preliminary, try running this, replacing <filename> on one of the files:
```

sed -i -e '/<cfset\ sName=ReplaceNoCase/,/<\/cfif>/c <div id="ap" class="button">' <filename>

```
That seems to work for me with a file I mocked up, but it may not work for real. If it does, try this from the toplevel directory you want to do the replacements in:
```

find . -iname '*.cfm" -exec sed -i -e '/<cfset\ sName=ReplaceNoCase/,/<\/cfif>/c <div id="ap" class="button">' '{}' \;

```

Of course, YMMV, Caveat Emptor, Backup your data, No implied warranty of fitness, etc. In other words, If you lose your data you have no one to blame but yourself.

---

### Post by OmahaVike on 2007-03-23
thank you tomchuk.  i think i'm getting there...

your first code snippet didn't work.  but the second one, i am able to work with as i'm actually using the cfif tags to extract out information.

a follow up question along the same lines.  i like the elegance of the sed command for replacing the strings, but would you (or anyone else, for that matter) be able to clue me in to how to delete an entire line based on this?

```

<cfset sName=ReplaceNoCase(Replace("Ubuntu Forums Rock","&nbsp;"," ", "ALL"),"<br>","","ALL")>

```

i'd hope the command would be generic enough where it would simply wipe out the entire contents after the "<cfset" string, to the end of the line, despite what is in the middle.  obviously, i cannot use the closing ">" as a determinant.

thanks again for your help thus far, and i feel i'm getting closer to results.

---

### Post by tomchuk on 2007-03-23
This will delete any line with "<cfset" in it:
```

sed -i -e '/<cfset/d' <filename>

```

This will remove "<cfset" and everything after it, 'till the end of the line, leaving anything before "<cfset":
```

sed -i -e 's/\(^.*\)<cfset.*$/\1/g' <filename>

```

---

### Post by OmahaVike on 2007-03-23
found it....

find . -iname "filename.html" -exec sed -i -e '/<cfset*/d' '{}' \;

thanks for the pointing me in the right direction.  best of luck to all.

---

