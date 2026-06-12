---
title: "[SOLVED] Problem with Synaptic"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Iklaad on 2008-03-20
I'm new to Ubuntu (7.10).
The problem is when I try to open Synaptic I get the below error message and when I click close on the pop-up, Synaptic closes.

E: Type '<!DOCTYPE' is not known on line 3 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Any help would be much appreciated.

---

### Post by wormser on 2008-03-20
Post the results.

```
gedit /etc/apt/sources.list.d/medibuntu.list
```

and

```
gedit /etc/apt/sources.list
```

---

### Post by Iklaad on 2008-03-20
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" ><head><title>Website Suggestions</title>

    <meta http-equiv="content-type" content="text/html" charset="UTF-8" />
    <meta name="robots" content="nofollow" />
    <link rel="stylesheet" type="text/css" href="dnsStyle.css" />
    <link rel="stylesheet" type="text/css" href="tw_main.css" />
</head><body>
<div id="wrapper">
<table border="0" cellpadding="0" cellspacing="0" width="100%" class="tw_header">
  <tr>
   <td width="202" height="59"><a href="http://www.rr.com/"><img name="rrHeaderLeft" src="img/rrHeaderLeft.jpg" width="202" height="59" border="0" id="rrHeaderLeft" alt="Go to Road Runner Portal" /></a></td>
   <td width="300" height="59" background="img/rrHeaderMiddle.jpg">&nbsp;</td>
   <td background="img/rrHeaderExpansion.jpg"><img name="rrHeaderExpansion" src="img/rrHeaderExpansion.jpg" width="1" height="59" border="0" id="rrHeaderExpansion" alt="" /></td>
   <td width="1" height="59"><img name="rrHeaderRight" src="img/rrHeaderRight.jpg" width="1" height="59" border="0" id="rrHeaderRight" alt="" /></td>
  </tr>
</table>
<script type="text/javascript">
    // <!--
        function toggleDetails()
        {
            if(document.getElementById('whatsthis').style.display == 'none') {
                document.getElementById('whatsthis').style.display = '';
            } else {
                document.getElementById('whatsthis').style.display = 'none';
            }
        }
    // -->
</script>
<script language='Javascript'>
				function checkForEmptySearchBox(textField) {
					if (textField.value == '') {
						window.location = window.location;
						return false;
					} else {
						return true;
					}
				}
			</script>
			<table border='0' cellpadding='0' cellspacing='0' align='center'>
			  <tr>
				<td width='480' id='search'>
				  <!-- Nested Search Box and button -->
				  <form action='index_results.php' onSubmit='return checkForEmptySearchBox(querybox);'>
					<table width='480' border='0' cellspacing='0' cellpadding='0'>
					  <tr>
						<td><img src='/img/blank.gif' width='420' height='1'/></td>
						<td><img src='/img/blank.gif' width='60' height='1'/></td>
					  </tr>
					  <tr>
						<td><input size='70' type='text' class='searchfields' name='querybox' value=''/>
</td>
						<td align='center'><input type='submit' value='Search' class='searchbutton' size='50px'/></td>
					  </tr>
					</table>
				  </form>
				  <!-- Nested Search Box and button -->    </td>
				<td width='90' valign='top' align='right'><img src='img/stacked_left_ascii.gif' alt='Powered by YAHOO! Search' width='84' height='24'/></td>
				<td width='8' height='24'>&nbsp;</td><td id='whyAmIHere' valign='top'>
<a href='#' onclick='toggleDetails();return false;' title='Why Am I Here?'> Why Am I Here?</a>
</td>
</tr>
			  <tr>
				<td height='10' colspan='3'><img src='/img/blank.gif' width='64' height='1'/></td>
			  </tr>
			</table><div class="whatsthis" id="whatsthis" style="display:none;">

    <hr align="center" width="99%" size="1" noshade="noshade" />

    <table class=why_wrapper>
        <tr>
            <th class=why_wrapper>
                <div style="float:right; font-weight:bold"><a href="#" onclick="toggleDetails();return false;">[X] CLOSE</a></div>
                <span class="question">Why am I here?</span>
            </th>
        </tr>

        <tr>
            <td class=why_wrapper>

                You entered an unknown web address that was used to present
                site suggestions that you may find useful. Clicking any of
                these suggestions provides you with search results,
                which may include relevant sponsored links.

                <br /><br />

                If this service is not right for you, please visit your
                <a href="prefs.php">Preferences</a>
                page to opt out. At any point in time, you can opt back in to the
                service by visiting your <a href="/prefs.php">Preferences</a> page.

                <br /><br />

                If you have other questions about this service, please visit our
                <a href="faq.php">FAQ</a>.
				
				<br /><br />

                For further assistance, please go to <a href="http://help.rr.com" target="_new">http://help.rr.com</a>.
				
				<br /><br />
            </td>
        </tr>
    </table>
<hr align="center" width="99%" size="1" noshade="noshade" />
</div>
<table class=d2r_wrapper><tr><th class=d2r_wrapper>Sorry, we couldn't find <span style=color:#BE0A00>www.medibuntu.org</span></th></tr></table><table class=middle_pane>
<tr>
    <td width=75% valign=top>
        <table class=results_left>
            <tr><th class="d2r">Sponsored Results</th></tr><tr><td class=d2r>
 <br />No sponsored results found.<br/><br /> </td></tr>
</table>


 
 <table class=results_left_bottom>
 <tr><th class=d2r>Web Results</th></tr>
<tr><td class=d2r>
 <br />No web results found.<br/><br /></td></tr>
</table>
 </td>
 
    <td width=25% valign=top>
            <table class=results_right><tr><th class=d2r>Related Searches</th></tr><tr><td height="10"></td></tr>
<tr><td class=d2r_results_right>No Related Searches Found.</td></tr>            <tr><td height="10"></td></tr></table>
            <table class=results_right><tr><th class=d2r>Popular Categories</th></tr><tr><td height="10"></td></tr>
<tr><td class=d2r_results_right><a href="index_results.php?querybox=Travel" class="sidelinks">Travel</a></td></tr>
<tr><td class=d2r_results_right><a href="index_results.php?querybox=Financial+Planning" class="sidelinks">Financial Planning</a></td></tr>
<tr><td class=d2r_results_right><a href="index_results.php?querybox=E+Commerce" class="sidelinks">E Commerce</a></td></tr>
<tr><td class=d2r_results_right><a href="index_results.php?querybox=Lifestyle" class="sidelinks">Lifestyle</a></td></tr>
<tr><td class=d2r_results_right><a href="index_results.php?querybox=Real+Estate" class="sidelinks">Real Estate</a></td></tr>
        <tr><td height="8"></td></tr>
<tr><td class=d2r_results_right><a href="index_results.php?querybox=Insurance" class="sidelinks">Insurance</a></td></tr>
<tr><td class=d2r_results_right><a href="index_results.php?querybox=Business" class="sidelinks">Business</a></td></tr>
<tr><td class=d2r_results_right><a href="index_results.php?querybox=Legal+Help" class="sidelinks">Legal Help</a></td></tr>
<tr><td class=d2r_results_right><a href="index_results.php?querybox=Personal+Finances" class="sidelinks">Personal Finances</a></td></tr>
<tr><td class=d2r_results_right><a href="index_results.php?querybox=Computers" class="sidelinks">Computers</a></td></tr>
        <tr><td height="8"></td></tr>
<tr><td class=d2r_results_right><a href="index_results.php?querybox=Health+Care" class="sidelinks">Health Care</a></td></tr>
<tr><td class=d2r_results_right><a href="index_results.php?querybox=Shopping" class="sidelinks">Shopping</a></td></tr>
            <tr><td height="10"></td></tr></table><!--</td></tr>-->
    </td>
</tr>
</table>
<table class=d2r_wrapper>
<tr><th class=d2r colspan=12>Popular Results</th></tr>
<tr>
<th class=d2r_bold><a href="index_results.php?querybox=Travel">Travel</a></th><th class=d2r_bold><a href="index_results.php?querybox=Financial+Planning">Financial Planning</a></th><th class=d2r_bold><a href="index_results.php?querybox=E+Commerce">E Commerce</a></th><th class=d2r_bold><a href="index_results.php?querybox=Lifestyle">Lifestyle</a></th><th class=d2r_bold><a href="index_results.php?querybox=Real+Estate">Real Estate</a></th></tr><tr><td height="2"></td></tr>
<tr><td class=d2r_pop><a href="index_results.php?querybox=Airline" class="sidelinks">Airline</a></td><td class=d2r_pop><a href="index_results.php?querybox=Loans" class="sidelinks">Loans</a></td><td class=d2r_pop><a href="index_results.php?querybox=Domain+Names" class="sidelinks">Domain Names</a></td><td class=d2r_pop><a href="index_results.php?querybox=Fitness" class="sidelinks">Fitness</a></td><td class=d2r_pop><a href="index_results.php?querybox=Mortgages" class="sidelinks">Mortgages</a></td></tr><tr><td class=d2r_pop><a href="index_results.php?querybox=Car+Rental" class="sidelinks">Car Rental</a></td><td class=d2r_pop><a href="index_results.php?querybox=Credit+Cards" class="sidelinks">Credit Cards</a></td><td class=d2r_pop><a href="index_results.php?querybox=Web+Hosting" class="sidelinks">Web Hosting</a></td><td class=d2r_pop><a href="index_results.php?querybox=Dating" class="sidelinks">Dating</a></td><td class=d2r_pop><a href="index_results.php?querybox=Refinancing" class="sidelinks">Refinancing</a></td></tr><tr><td class=d2r_pop><a href="index_results.php?querybox=Hotels" class="sidelinks">Hotels</a></td><td class=d2r_pop><a href="index_results.php?querybox=Debt+Consolidation" class="sidelinks">Debt Consolidation</a></td><td class=d2r_pop><a href="index_results.php?querybox=Web+Design" class="sidelinks">Web Design</a></td><td class=d2r_pop><a href="index_results.php?querybox=Singles" class="sidelinks">Singles</a></td><td class=d2r_pop><a href="index_results.php?querybox=Home+Equity+Loans" class="sidelinks">Home Equity Loans</a></td></tr><tr><td class=d2r_pop><a href="index_results.php?querybox=Cruises" class="sidelinks">Cruises</a></td><td class=d2r_pop><a href="index_results.php?querybox=Stocks" class="sidelinks">Stocks</a></td><td class=d2r_pop></td><td class=d2r_pop><a href="index_results.php?querybox=Education" class="sidelinks">Education</a></td><td class=d2r_pop><a href="index_results.php?querybox=For+Sale+by+Owner" class="sidelinks">For Sale by Owner</a></td></tr><tr><td class=d2r_pop><a href="index_results.php?querybox=Vacations" class="sidelinks">Vacations</a></td><td class=d2r_pop><a href="index_results.php?querybox=Payday+Loans" class="sidelinks">Payday Loans</a></td><td class=d2r_pop></td><td class=d2r_pop><a href="index_results.php?querybox=Degrees" class="sidelinks">Degrees</a></td><td class=d2r_pop><a href="index_results.php?querybox=Credit+Score" class="sidelinks">Credit Score</a></td></tr></table>
<br/><br/><p/><script language='Javascript'>
				function checkForEmptySearchBox(textField) {
					if (textField.value == '') {
						window.location = window.location;
						return false;
					} else {
						return true;
					}
				}
			</script>
			<table border='0' cellpadding='0' cellspacing='0' align='center'>
			  <tr>
				<td width='480' id='search'>
				  <!-- Nested Search Box and button -->
				  <form action='index_results.php' onSubmit='return checkForEmptySearchBox(querybox);'>
					<table width='480' border='0' cellspacing='0' cellpadding='0'>
					  <tr>
						<td><img src='/img/blank.gif' width='420' height='1'/></td>
						<td><img src='/img/blank.gif' width='60' height='1'/></td>
					  </tr>
					  <tr>
						<td><input size='70' type='text' class='searchfields' name='querybox' value=''/>
</td>
						<td align='center'><input type='submit' value='Search' class='searchbutton' size='50px'/></td>
					  </tr>
					</table>
				  </form>
				  <!-- Nested Search Box and button -->    </td>
				<td width='90' valign='top' align='right'><img src='img/stacked_left_ascii.gif' alt='Powered by YAHOO! Search' width='84' height='24'/></td>
				<td width='8' height='24'>&nbsp;</td></tr>
			  <tr>
				<td height='10' colspan='3'><img src='/img/blank.gif' width='64' height='1'/></td>
			  </tr>
			</table>  <hr align="center" width="99%" size="1" noshade="noshade" />
  <div id="nxd_footer">
    <div id="opt_out_link"><a href="prefs.php" title="Opt In or Out of this Service">Opt In or Out of this Service</a></div>
    <div style="float:left">&nbsp;&nbsp;&nbsp;&copy; 2008 Road Runner HoldCo LLC. All rights
reserved.</div>  </div>
</div>
</div>
</div>
</body></html>

------------------------------------------------------------------------------------------------------------

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

---

### Post by PmDematagoda on 2008-03-20
Remove the file in question with:-
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```
and then reload the sources list with:-
```
sudo apt-get update
```
That should fix the problem.

---

### Post by mikewhatever on 2008-03-20
That's html code and not repositories. Run <sudo rm /etc/apt/sources.list.d/medibuntu.list> and follow this guide [https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29](https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29).

---

### Post by Iklaad on 2008-03-20
ok that worked thanks for the quick replies

---

### Post by wormser on 2008-03-20
They beat me to it.

---

