---
title: "How to make the folder view CONSTANT, not change when switching folders."
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-10-11
When changing around folders, it changes from icon view to list to whatever..

I just want it to be constant no matter what folder im in.. If i change the view to icon in the current folder, then the next folder i enter will have the view i just changed it to.

---

### Post by systemintheglitch on 2006-10-11
I also want the zoom level to be constant, and the sidebar status.

---

### Post by systemintheglitch on 2006-10-11
> **systemintheglitch said:**
> I also want the zoom level to be constant, and the sidebar status.


Also, the status of showing hidden files or not.

---

### Post by systemintheglitch on 2006-10-11
> **systemintheglitch said:**
> Also, the status of showing hidden files or not.


Im in the default ubuntu file browser.

---

### Post by jem7v on 2006-10-11
Open Nautilus (the default file viewer).

Edit -> Preferences...

You can set all your defaults for viewing in there. It's a bit like the "Folder Options..." dialogue in Win98.

---

### Post by systemintheglitch on 2006-10-11
doesnt have the option im talking about.. I think.

---

### Post by jem7v on 2006-10-11
1. If you want it to change the default viewing mode Every time you change the icon/list/sort features of an individual folder, um, I'm not sure there's a quick way to make it do that.
2. Showing hidden files or not: there is a "show hidden files" option in the View menu at the top. Alternatively, just hit Ctrl+H to toggle this option.

Does that help at all?

---

### Post by smyrman on 2007-05-26
> **systemintheglitch said:**
> doesnt have the option im talking about.. I think.

Well no it doesn't;-( realy anying though.. who would want the folder view to change eace time one change the directory?? I mean, if I am browsing with list-view, I am browsing with list-view!

**If u like u can try Thunar **(the xfce file-manager - veary simular to nautilus). It currently does not have the annoying feature of "remembering folder view"=)

U can download it by searching for "thunar" in Synaptic. It migth also be a good idea to add some thunar plug-ins:)

**To make Thunar your default browser(almost)** is only slightly harder (and unconviniant).. However, here are one aproch that i extracted from[ this site]("http://assente.altervista.org/it/use_thunar_as_default_gnome_file_manager/") :
[B]
WARNING: this script seams to bee somwhat buggy..[/B]

- Please follow these 3 steps in the correct order

**1 first write these 3 lines of code in a terminal:**
sudo apt-get install ruby
sudo mv /usr/bin/nautilus /usr/bin/nautilus.real
sudo gedit /usr/bin/nautilus

**2 It will now open a "gedit" window... paste this code in the new window:**

[I]
#!/usr/bin/ruby

# nautilus - Replacement shell script to use Thunar
# in place of nautilus as much as possible - thanks assente

$KODE='U'

# searches for a binary in $PATH
def which(app)
    dirnames = ENV['PATH'].split(':')
    dirnames.each { |dirname|
        filename = File.join(dirname, app)
        if (File.executable?(filename) and
            File.file?(filename))
            return filename
        end
    }
    return nil
end

## we need the explicit path to tell exec in arg 0
## so that when thunar/nautilus takes control of
## the process, the right name is shown in the
## process list / pidof / &c, else 'pidof thunar'
## returns null

## set the path explicitly
thunar_bin = '/usr/bin/thunar'
## else uncomment below
#thunar_bin = File.which('thunar')

## set the path explicitly
nautil_bin = '/usr/bin/nautilus.real'
## else uncomment below
#nautil_bin = File.which('nautilus.real')

args = []

if (ARGV.empty?):
    exec([thunar_bin, thunar_bin])
else
    ARGV.each { |arg|
        if (['--no-desktop', '--browser'].include?(arg))
            args.push(arg)
        end
    }
    args.each { |arg| ARGV.delete(arg) }
end

if (ARGV.empty?):
    exec([thunar_bin, thunar_bin])
elsif (ARGV[0][0,1] == '/')
    exec([thunar_bin, thunar_bin], ARGV[0])
elsif (ARGV.length > 1 and ARGV[1][0..6] == 'file://')
    exec([thunar_bin, thunar_bin], ARGV[1])
else
    unless (args.include?('--no-desktop'))
        args = ['--no-dekstop'] + args
    end
    exec([nautil_bin, nautil_bin], *(args + ARGV))
end[/I]

**Close the "gedit" window, and save the changes**

**3 Now, copy this line to a terminal:**
sudo chmod a+rx /usr/bin/nautilus

**U should now have set Thunar as your default file browser. Hope this helps=) To undo these changes, type this in a terminal:**
sudo mv /usr/bin/nautilus.real /usr/bin/nautilus

---

### Post by meng on 2007-05-26
Look again at Nautilus preferences, as jem7v said. The first tab that comes up has two options:
default view (drop-down list)
view hidden/backup files (checkbox)

If you don't have those options, then you're looking in the wrong place!
If your folder views don't change, it may be because you've already specified a particular view for a particular folder. Try navigating a folder you haven't been to before.

---

### Post by smyrman on 2007-05-26
> **meng said:**
> Look again at Nautilus preferences, as jem7v said. The first tab that comes up has two options:
default view (drop-down list)
view hidden/backup files (checkbox)

If you don't have those options, then you're looking in the wrong place!
If your folder views don't change, it may be because you've already specified a particular view for a particular folder. Try navigating a folder you haven't been to before.

I don't think u quite got it.. the problem is, we do not want nautilus to remember the folder view for each folder.. meaning:

- when I browse with icon-view in nautilus, ALL FOLDERS are supposed to have icon-view
- when I browse with list-view in nautilus, ALL FOLDERS are supposed to have list-view

currently, this function is not supported in nautilus (the function not to remember folderview for each individual folder).. it MIGHT be supported in an earlier version however..

In thunar however, it is..
and in konqueror (for KDE) and windows explorer too..

---

