---
title: "perl Tk Doubt"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by srikrishnan on 2008-02-06
Hi All,

I have written a perl script using Tk module.

In that my requirement is, if a user select a folder from list of the first "OptionMenu" then in the second "OptionMenu" all the subfolders should be listed.

But I am not able to succeed, I don't know how to use  "configure". Can anybody help me in this regard

FYR: Below I have pasted my perl code

use strict;
use warnings;
use Tk;
my ($filepath, $var, $var1, $TagType);
my $BrowseFrame;
my @allCUP;
my @allJRN;

my $mw = new MainWindow;
$mw -> title ("Extraction/PDF From APP");

my $mainFrame = $mw -> Frame -> pack (-padx => '15', -pady => '15');

my $label = $mainFrame -> Frame -> pack(-side => 'top');
$label -> Label (-text => 'Extraction/PDF From APP',-background => 'white', -foreground => 'blue', -font => 'Impact 20', -pady => '5') -> pack;;

opendir(HOMEDIR, "H:/") ||die ("Unable to open Publisher H:/ directory");
my @allPubls = readdir (HOMEDIR);
closedir(HOMEDIR);

my $PublFrame = $mainFrame -> Frame -> pack (-side => 'top', -pady => '10');
my $opt = $PublFrame -> Optionmenu(-menu => $BrowseFrame, -options => [@allPubls], -command => \&gotoConv, -variable => \$var,)->pack(-side => 'left');

opendir(JRN, "H:/$TagType/") ||die ("Unable to open Publisher H:/ directory");
@allJRN = readdir (JRN);
closedir(JRN);

my $JrnlFrame = $mainFrame -> Frame -> pack (-side => 'top', -pady => '10');
my $opt1 = $JrnlFrame -> Optionmenu(-menu => $BrowseFrame, -options => [@allJRN], -variable => \$var1,)->pack(-side => 'left');
$opt1 -> configure (-options => [@allJRN]);
$opt1 -> update ();

$BrowseFrame = $mainFrame -> Frame -> pack (-side => 'top', -pady => '10');
$BrowseFrame -> Button (-text => 'Browse', -command => \&gotoOpen) -> pack (-side => 'left');
$BrowseFrame -> Entry (-textvariable => \$filepath, -width => '60') -> pack (-side => 'left');

my $finalFrame = $mainFrame -> Frame -> pack (-side => 'top');
$finalFrame -> Button (-text => 'Ok', -command => \&gotoProcess) -> pack (-side => 'left', -padx => '2');
$finalFrame -> Button (-text => 'Cancel', -command => sub {$mw -> destroy}) -> pack (-side => 'left', -padx => '2');

MainLoop;


sub gotoOpen {
	
}

sub gotoConv {

	$TagType = shift;
#	print "H:/$TagType/\n";
	


}


Thanks in Advance,
Srikrishnan

---

