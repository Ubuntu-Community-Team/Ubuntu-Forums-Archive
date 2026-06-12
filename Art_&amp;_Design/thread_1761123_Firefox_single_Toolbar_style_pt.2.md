---
title: "Firefox single Toolbar style pt.2"
date: 2011-05-17
forum: Art &amp; Design
---

### Post by arzali on 2011-05-17
Update from this [http://www.omgubuntu.co.uk/2011/04/give-firefox-4-a-internet-explorer-9-makeover/](http://www.omgubuntu.co.uk/2011/04/give-firefox-4-a-internet-explorer-9-makeover/)

Changes: make URL bar bigger when it is focused 
[[IMG]http://uppix.net/f/e/d/de489029a80781eefaa64840bbd2ett.jpg[/IMG]]("http://uppix.net/f/e/d/de489029a80781eefaa64840bbd2e.png")

```
#main-window[sizemode="maximized"] #tabbrowser-tabs
{
max-width: 1020px !important;/*Change the size untill you can see all your tabtoolbar icons!!!!!!!!!!!*/
min-width: 1020px !important;/*Change the size untill you can see all your tabtoolbar icons!!!!!!!!!!!*/

}




#main-window[sizemode="maximized"] #urlbar[focused="true"]  {
min-width: 800px !important;
max-width: 800px !important;

}




#urlbar{
max-width: 300px !important;
min-width: 300px !important;
height: 26px !important;
  margin-bottom: -2px !important;
  margin-top: 0px !important;
}

#main-window[sizemode="normal"] #urlbar-container{
max-width: 305px !important;
min-width: 305px !important;
}

/*short verified icon
.verifiedIdentity
{
max-width: 26px !important;
min-width: 26px !important;

}*/


.unknownIdentity, .chromeUI, .urlbar-history-dropmarker{
  -moz-appearance: none !important;
display:none !important;

}

#page-proxy-favicon{
height: 25px !important;
width: 25px !important;

}


#TabsToolbar
{
height: 28px !important;
  border-bottom: 5px !important;
}

```Firefox big elementary buttons
```


/*Navigation buttons based on softwarecenter*/
#back-forward-dropmarker { 
display: none !important; 
}

#back-button toolbarbutton,
#unified-back-forward-button toolbarbutton {
  -moz-appearance: none !important;
  border: none !important;
  padding: 0px !important;

}


#unified-back-forward-button {
  -moz-padding-start: 0px !important;
  margin-bottom: -2px !important;
}

toolbar[iconsize="small"][mode="icons"] #back-button {
  list-style-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAD8AAAC5CAYAAACftucaAAAAAXNSR0IArs4c6QAAAAZiS0dEAAAAAAAA%2BUO7fwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9oLChI0Gj72OQ8AABk9SURBVHja7V17bFTHuf%2Fmcc7Zt%2B31rl%2Fx22YxGIdYDSGAjTHBoY%2B0zYNCI9SgJqVqpRJVFUpatShS%2F0hTqQ1tbhpFJa1Eqqu0JXArpUQ0cNuYRwqGEMAx4AcUWBdsr71re9e7Z885M3P%2F2LNmQ8BeJ6i75O5PGq0f5%2Bzub75vZr6Z%2BX5nEKQHBAAEAOi6detqXS5XncViqQAALMuyGwBA07QgAHBVVf2Tk5MX3nzzzYsAYAAAAwABWQiaDun6%2BnpbS0tLi9PpbFqxYkXN%2FPnzPWVlZU5CiK2goIACgAiFQowxFr169Wq4t7d3tLS09F%2FhcLj78OHDhwcGBqLZWAlohv9hAJA2bdrUVlZW1vrQQw%2FVNzc3l1mtViSE0AFAM6%2FTzVfJfJURQlIsFhMffPDB1b%2F%2B9a8DV69ePbRz585O81qeLeTJrf7e0dFR1NbW9uDDDz%2F88BNPPNFcV1dnwxhPCSGiQghNCMHMAmZJ%2Fq4JIVRCiF5ZWVmwdOnSGovFUma1WonX6x27ePFiLFs84Gbkyfr16%2Bd5PJ6VW7Zseaytra2CUhrhnKtz%2FNJCCKHJsmw0NDSUVFVV1Zw%2Ff97w%2BXxqT09PKBsq4EbyuL293eP1ett%2B%2FOMfP7JgwYJ8xtikEOITu6oQgnPO1dLS0rxFixbVHj16NFxQUHD10qVLGfcAckP7l1tbW9du2bLlsQULFjg451O364OEEJrb7bZVVFTUnDt3LnLmzJmBTLf%2FVPJ048aNq9etW%2FdwW1tbCWNsSiQAt7EYZWVleZRSLyFkqru7%2B1ImKwAnrd7Q0GAvLi5uaW9vrzQMI8w55%2BI2g3PODcMIt7e3VxYXF7c0NDTYZxlx%2FiPkSXNz84pHHnmk3mKxqJxzNldinZ2drq1bt85LowKYxWJRH3nkkfrm5uYVM4w4%2FxHyyOVyyS6Xa8k999xTYBhGfK7u3NnZmffzn%2F%2F8bl3XXelcbxhG%2FJ577inIz89fUlpaasmU9SkAoFWrVvkeeOCBckqpzhhLuweORqP417%2F%2Bdc177713l91utxNC4kKItO6nlOrt7e3lg4OD9W%2B99daZTPT8FACw1Wqtq6%2Bvd3LO9XSHtZ6eHvv27dsbJiYm3Ha7XZYkCRBCkO79nHO9vr7eabPZ6gDgw0x0fBQAEKW0qKCgQOac89kswDmH119%2FvXzfvn01hBCH1WolpiUBISTStSDnnBcUFMiU0qKMuj3G2OVyuagQIjaT146MjMjbt2%2F3%2Bf3%2BYqvV%2BpG2mrwvUX9pTCoQYi6XS8YYuzJJHgBAlmUZOOe3ZD48PCz%2F6le%2F8vn9%2FmJFUWbqpNKyvBACZFkGAJAzOqXlnCfbqpjBUlJ%2Bfn5hMBi0zsZrjqFvxiI8DADAGNNUVeUpX%2F5jpaioKPzNb36zq7a2dnIW4ukWUFWVM8a0TJIXuq5PTkxMGMmp2K1QVFQU37Zt29Unnnhi3GazcUqpSJbkEJduUAQAMDExYei6PpmpCQ4GAKFpWmBsbCyOEEIzWUsIEY%2FH4%2BdWrlzZs23btpGqqiqdUgqUUpAkCQghaVsfIYTGxsbimqYFMkmeT01NDfT19UUwxiQdq%2Bm6Pux2uz949tlnrzz44IMRSZKAUgpzCYcxxqSvry8yNTWVsdkdBgDR3d09sHfv3qFoNCphjBFCSMxWhBBRznn3ww8%2FfP7JJ58MSpIEGGNI516MMYpGo9LevXuHuru7BzLq9oFAQJ2YmDh%2B6tSpcUIInUOnxTRNu9zU1HT6ySefDGqahtK5jxBCT506NT4%2BPn4iEAiomSJPUnrp0dHR0cZVq1aVWywWzWyXkE4RQsRKSkom165dGxJCRGa6lhCCI5GI45e%2F%2FGX%2FmTNn%2FhwMBmOZntKKgYGB8MjIyOEDBw4MEULs5pcV6RbO%2BRhj7Nos7i4IIfYDBw4MDQ0NHR4YGAhncikrdS4tLl686I9EIlJtbW1dZWWllXN%2BW8dgSqmjq6tLffnll%2Fft37%2F%2Fb%2BamRtYsYAqn0xk4efIkWrx4cXVJSYkdADTTcvApCqKUOs%2BePRt%2F7rnn3hkdHf370NBQRq1%2BU%2FLDw8NqWVmZ%2Bu6776q1tbWVVVVVeeYmBftEuyIISZTS%2FKNHj04999xz%2B1VV7erq6vJnw%2BbFzZaQxJUrV0JOp3Ooq6srTggprKqqKrHb7dR007S8AGNMKKWuyclJ51%2F%2B8hf%2FSy%2B99M7Y2Njfjx8%2F7v%2BkFXm7Met21apVq9q8Xm%2FLpk2bypcvX15kt9uZECIuhIgDABdCGKaFKQBghJCCEFKmpqbIe%2B%2B9N7Jz587BQCBw5N133%2B2ExBZX1mxXoTT%2BT8rLy%2B11dXUrrFZr0xe%2F%2BMXKxsZGZ2VlpZUQ4qqoqAAA4H6%2FHzPGJq9cuRLr6ekJv%2F3221disVj3hQsXjgwODk7BHbZR%2BbFKAAC6dOnSWqvVWidJUgUAYEppIQCAYRhjAMB1XffHYrELx44dy%2FotavQJrk8WfJP7henWH5m65pBDDjnkkEMOOeSQQw455JBDDjncLvy%2FXsyY8zLWZ0lpkdYCZqrSor6%2BXp4%2Ffz7z%2BXwMYywqKioYAIDf7yecc9TX10d6e3vJwMCA9plQWni93mXLli0zOjo64k6nMyKEmASAZEZFMjM7mUfrQgi5wuGwY%2F%2F%2B%2Fco%2F%2F%2FlPGggE%2FpmNSotbkScdHR3e8vLy1qVLl85ft26d6na7RzjnVwEgnuZ7KxjjsmAwWPTmm29ajh071js4OHho%2F%2F79AciSTYsZlRbr16%2Bv2bBhw4iiKH2MsREhhDGX9HLOechqtQbvvfdearFYKvx%2Bv%2FeOUFp897vfLWttbb2k6%2FoFzrn2SXPsOec6Y2zU5%2FPxsrKyitOnT7uyWmnxta99raa1tbVX07TB25VrzxgbLy8v12RZrvX7%2Fc6sVFosX7588YYNGy7G4%2FHB2y04YIxNNTQ0wMjIiC8%2FP1%2FKKqWF2%2B1e9thjjwVUVb3MGDP4bQZjzFBV9fJjjz0WcLvdy7JKadHa2qo7HI5%2BXdfjjDE%2Bl7J79%2B78LVu2NM12na7rcYfD0d%2Fa2qpnldKivb3936qqjn8C4gW7d%2B9epihKfjrXq6o63t7e%2Fu%2BsUVo0NTUhRVEuR6PRtPNkJiYm8C9%2B8YsFfr%2B%2F1uv1OiilUcbYrG2YMcZtNtvlxsbG6qxQWtTW1k5pmhZhjKUVgHR2drr%2B%2BMc%2FNlNKiwoLCy2EEGG267Tu1zQtUltbO5UVSouioqIxTdO0dCz34osv1vX39y%2FIy8tzSZJEAUBgjAEARDr3m%2BS1oqKisaxQWng8nl5d17WZBAf9%2Ff2W1157bbGu6xVer9dmJk9z05WBEJI2eSGE5vF4ghjj%2BZBppYXNZguHw2F2K3VUb2%2Bv5Xe%2F%2B10TY%2Bwul8tluVklmR1aWm7POUdOpzMMWaK0YIwxfivykiRJdXV1RYFAwJaycHEjIZ6u5VEie5llhdIiHA5bzCjspsNTeXl5aPXq1f%2Fr8XiCM6glRbrDoxBChMNhSyaVFhRMpUUgEHB7PB4Uj8dv6bb19fVTy5Ytu%2FiPf%2Fyj8u2333YbhjHdVnVdByEENwwjLbeXJIkEAgF3JpUWFEylxfDwcElJSQmeyW0jkUgsEomcWL58%2BbWGhobG119%2FvXhkZEQBACCEQNLyaX0wpXh4eNitadoQZFpp0d%2Ffn2%2B1Wq3puKzf7%2FdLknToBz%2F4Qd%2BKFStChBCRMs6nVaxWq7W%2Fvz8%2Fk0oLYlo0oijKira2tinDMIZ0XZ9VRR2LxeLhcHjw%2FvvvVz0ej7Wnp8eu63r4vvvuOz%2FbvYqiEIzx%2FD%2F84Q93HTt2bG80GtUyZflppcXBgwfnFRYWOtK1XjweN3p7e3sbGhqOPP7440PxeBzSua%2BwsNBx8ODBeVmltIhEIivb2tqYLMtDU1NTRrrz9FAoFPH5fGNf%2BcpXAoFAYHymawsLC2UhxD2%2F%2Fe1vq3p6et7MpNJiejoZDAaNsrIyORaLNbW3t4%2BNj4%2BHdF1PezEjGAxGRkdHZyQuyzLU1NRU79y5c8nZs2dPnDhx4nwmFzM%2BprTAGBfZ7faGpUuXhq5duxa6nSs5jY2NVfv27VuxZ8%2BewaxVWvT391dUVVVVLlmyRA0Gg3PygJvBYrGgxYsX1x47duzeV155JZr1Souurq4Su93uW7VqFZNlOTw6Ohr%2FJMTr6urs9fX189966637X3nllegdo7Q4d%2B6cZ2hoaFFzc7Pb5%2FMJjHEkFAqltXZfXV2tNDY21uq6%2FrlXX321cffu3VfvSKVFXl7e%2FZ%2F%2F%2FOfHH3300SGXyzWk6%2FpoNBoNRaNR7fz581FFUVBNTY3VZrPJNputQJIkz%2BTkZMmePXtK9u3blz8xMXHsM6G0uPvuu1FTU1N40aJF47IsS%2FPmzZsAANHf35%2BvaZr%2B4Ycf5nd3dzvPnDkjckqLnNIihxxyyCGHHHLIIYcccsghhxxyyCGHT43%2F10qLOZ9psWbNmgafz1dSXFycRwixORwOCQBEJBIxGGPR4eHhib6%2BvqHS0tLznwmlRUVFxcpHH320aeHChZWKomDzwUDJrSbjhoqkCCEaj8f52bNnr%2BzZs6fb7%2FcfvCPPtNi4cePXN27cuKK8vNyFMU4%2BGckwSaQSSf5uCCE0QggrLS11L1u2zFdQUHAXpVTcUWdaPPPMM08sWbKkjhASE0JoMPczLXRKKa%2Btrb2roaGhvru7O3ZHKC1%2B%2BtOffqOmpsYjhJj6lF9UmAmH%2BZ%2F73Od8hw8fHstqpcUzzzzzRG1trds8weS2QAhh5OXlOXw%2BX113d3coK5UW3%2FjGN75%2B3333VQkh1HSfVT8HMK%2FXm%2B90Or1CiImsUlqUlZW1trS0zOOcx1KefX3bivls61hLS8u8srKy1qxSWmzYsKFJlmVDCMHnqqI6cuSI%2FUc%2F%2BlF5GtdyWZaNDRs2NGWV0mLhwoXFjDF9rgkIR44csT3%2F%2FPO1qqra0hQa6QsXLizOGqXFl770pTpKKZ%2FLmRaxWAz%2F5je%2FKTl48KDHarVaCCF6mt2EoJTyL3zhC3XZcqZFAefcSLcDOn%2F%2BvHX79u0VY2NjLqvVSpNnWqR7P%2BfcqK%2BvL8iWMy1s6fTunHN44403vHv37i0FAIvFYsEAidxbU22R9uBfUFBgywqlhd1ul82Y%2FZYVEAgEpJdeeqn84sWLblmW5RvrKvXZ9ekY3263Z%2FRMi6SpZEmS8Kch%2FkniHvMzs0JpMaPVhBDEZrO5rFarPJs7z6UCskJpkSIyuGmA4vV6o0899dT5urq66GyE0iwQj8dZVpxpEYlE4mZvLWaoAO0nP%2FnJ6KZNm6ZsNptIHulAKZ0rcYEQgkgkEs%2BKMy1CodBUGh2PYRjGlba2tn9t27YtVF1dbaRWgHmmRdoLKaFQaCpbzrQI4cRYNavVGGMhr9c78Oyzzw6vXbs2ljzTYjbPSS0YY9zX1xfKijMtdu3adVlV1WSaWTqTFBUALn71q1%2B98tRTT01SSsUcyCNVVdGuXbsuZ82ZFmfPnh0hc%2FNdwRgbbmpquvCtb30rHI%2Bn9ywRQgg5e%2FbsSFYpLUZGRnwPPPBAjSzLDOZwpgUAxEtKSqIdHR1hAIjN8uh3HIvF5J%2F97GcnT506lT1nWly9evVQZ2fnJYyxZa5vxDmf5JwHZ%2BzhEuQtnZ2dlwYHBw9l3ZkWwWAQLVq0aF5paakTAPRPeZzDjVa3nTlzJvTCCy%2FszlqlxdGjR%2FX777%2B%2F1u12O80jHT6tdRDG2Hbx4sXxrVu37sl6pcX%2B%2FfsnFy1aVF1aWloAAManONSDEEIcp0%2BfHtu6deueO0ZpceTIkXB%2Bfn5hRUVFiaIo02dapGVqhDDG2B6LxZR9%2B%2Fb1P%2F%2F88%2F9zRyotSktLW7%2Fzne%2F4mpub77JYLAgSigkdEmdaMJMsSd4DALKqquKDDz7496uvvtp37dq1w58JpcX69evnNTY2FpaXl9sJIS6Px0MAgI%2BOjgrG2OTg4OBUT0%2FP2J%2F%2F%2FOf%2BnNIip7TIIYcccsghhxxyyCGHHHLIIYcccsjhU2NOKzmbN292AMDXAKANAO5GCFUCQAEklqomhBB%2BADgDAJ0AsGvHjh2RO5785s2bFyOEvgMAaxRF8RJCFEwwRYBIynsISDwA1WDMiMfj8QAAHBBCvLpjx47TdyT5zZs3v0ApfdxisRRhhBRMCJrekMBoepUusa8tgPNEminjTAgu4qqqjhiG8caOHTt%2BeMeQN639gtPpbEEI2QmhCBOc2NlECAAhQMmdfIQACQEcBCCARAUAgOAMdN0QADAVDocPCyF%2BmE1egG5BfBWl9CWnwzGfUioRQhEgBBgliGKMQYAABChh%2BBusL0TiFQQHIQAYM4RhGHo4HOk1DOPpHTt2vJuV5Ddv3rxYluX%2Fdjgc82VZpgRjQAQDhqS1zVcQAIABkElaAAjggERyzTpRCSAEcMaAcQaaphuRSKRX07SN2eABH5OWybL8Yp7L5ZNkmSbzbAgh026OUWLZXiQtLUTC%2FcFs%2FyjxNwAAwRNNgRMChHPAmFBMiG9yYuJFAHgg0%2BQ%2FslH57W9%2F%2BwW32%2F2orCiKoiiIUgqUJLKsCCGAzUIQBkIwYIzMnFsCaPpveDoPN1kIxoARBoIJIARYkqTiBQsWuN5%2F%2F%2F0DWUF%2B8%2BbNi51O5y9tNlu%2BxWJBScKEJshQShMkpskhwPg6ySRxjLE5EiSuM5MSAOHE6EAwQQKEJISYt2jRov0nT54czrjbW63W7zscDrfFYkGUUpNIguR07o3ZuyfbPZjujQCBu9ANNpsN%2FH4%2FpGagYoyT59kkCuZgQRbEOXcbhvF9APhmpsjjZOSGEFqrKApN5NQl8uqoRIAmXR4ToJhMJxsS07KEEPB4PdDS0gI1NTXXvYQQwAQDoYlrJEpBMpMVJUkCi0WhCKG1ZtSYOcvLsvx4YWFhvtVqRZJEASGS6NySLmxaHQFKGN8c1xHG0NDQADU1NeB0OiEUCgEm%2BPr2pEiM94AAuOCAEAaEefJ9UWFhYb5hGI8DwI6Mkbfb7V%2B2WBQqSRQIodPRG0Y4mWpmviLTXQQ481zQ1HQ3eD1eUBQFDGaAEAAYk0TTSA53ZiUggUCgxGuyUi0Whdrt9i9nlLyu642KYiWUSh%2Bxdkqe3TRxhACqqqrB5%2FOB0%2BkEAADGmdnORWIoRAniGPA0eSESNYIEAsEFIIRAUaxE1%2FXGjLq9YRhFlFJEKU04NkZmUAPTFSAAQJFkWNi4EMrKyoBSCh%2FPlb%2BxwhIdpECmrAwEEEFAYAFYYBBCIMMwijJN3ipJiR4%2BwR0n7JyM3wGBIsuwcOFCKC0tTU0x%2Fyh1BEAwBkDIHAjEdF%2BR0NQBABIguACBBFBKwTAMa0bJpyQJfqSNT1vQjPIkKdEsZlRHIAzTIyEgM9xNuHmyAhBBIAQHzm%2FwkkwMdZIkxTnn0wknqWM7QggwQqBpGnz44YcQCARuzRuhRLBjdpQYzGnvR7MwEz8DBs44SJIUzyh5RVFCnHOBpgezm3xZswIOHToEJ06cAMMwrgcuKZ4wPVIkozqEgKQOmSlTKs65UBQllFHyLpfriqZpTIjEfDx1sSK1Eggh4HA4YHhoCA4cOADBYDD1REKTPL5pxaW%2BF5h9gKZrzOVyXcko%2BaKiovdjsZjBmPGReS6Cj7s%2FIQQsVhtgjOHIkSNw7tw5YIxNh7T4BqtPlxtmz4wxiMViRlFR0fsZJd%2FR0fFGMBiM6rohuEgsU%2BCUL32dyHVLUkrB4XTApcuXoKurCxhjwDm%2Ffl9KhUFKUwJzGqzruggGg9GOjo43Mkq%2Burr6hMfjORcOhw3GuRmbJa9AH%2FcAnHBvjDDYbXaIRqfg%2BPHjEAwGzd4%2B0aElZ3eJyrv%2BoZwzCIfDhsfjOVddXX0io%2BQRQlpzc%2FOfQqFQRNPiieE4GdGJZPACN0R%2BMD2FVRQLTE1NweDg4HUvMXv5ZD%2BS2pzimiZCoVCkubn5TwihjOrqAABgzZo1u0pKSk6GJyfjzDCuVwAGSOiD8fWIDzAglAhmku5ssShgtVoTwxtCKR1n6uQIgWEYYnJyMl5SUnJyzZo1uzK5mIFThqjhp59%2B%2BoVYTL0cCoUMw9DNRUi4Hq2lDFPJ6X0yJphu06n9mhnvJ0cEXdchFAoZaix2%2Bemnn34BITScFeTNCjiwevXqnWNjY6PBYJBpmjY9jt%2F4%2BIfr%2FG7%2Be%2BoQyDkHTdMgGAyysbGx0dWrV%2B9ECGV0CeumC5gtLS2%2Fj0ajnkOHDj0uhPAUFhZSSZJQMoBJ1cjfGJreSDr5quu6GBsbM4LB4OjKlSvfaGlp%2BX02LF3Tm4Sow0KI%2F8rLy4u%2B8847GxhjFXl5eYrFYkGSJE0vTd0MN1pb13VQVVVMTEzEY7GY%2F6GHHvrT0qVLf5dpd591x0YIUQwAa15%2B%2BeVvXbt2bbHH43G4XC6auriZOhFKkmaMAWMMVFUVk5OTxujoaKS0tPT09773vdcA4EC2EE9rr04Iseb48eMPHjx4sG10dLTO7XbbnE4ntVgsRJIkhDFGZsQmDMMQqqqycDhsBIPBqMfjubBy5crOJUuWvJMNbXzO5FO84N7x8fEFf%2Fvb3%2B67fPlyXSgUKlVVNc8wDCtCiFNK44qiTBQUFFyrqqq6sHbt2q78%2FPxzAHAim6w9Z%2FIplSADwEIAqAaAYgDIAwCLOQ6qADAJAMMAcAkAzmYygMkhh1vj%2FwB8fOZy9F%2BAaAAAAABJRU5ErkJggg%3D%3D") !important;
  -moz-image-region: rect(0 35px 33px 0px) !important;
  padding: 0 !important;
  margin: 2px -14px 0 4px !important;
  position:absolute !important;
  z-index: 1 !important;
}
toolbar[iconsize="small"][mode="icons"] #back-button:not([disabled="true"]):hover:active {
  -moz-image-region: rect(150px 35px 183px 0px) !important;
}
toolbar[iconsize="small"][mode="icons"] #back-button:not([disabled="true"]):hover {
  -moz-image-region: rect(100px 35px 133px 0px) !important;
}
toolbar[iconsize="small"][mode="icons"] #back-button[disabled="true"] {
  -moz-image-region: rect(50px 35px 83px 0px) !important;
}

toolbar[mode="icons"] #forward-button {
  -moz-appearance: none !important;
  padding: 0 !important;
  border: none !important;
}

toolbar[iconsize="small"][mode="icons"] #forward-button {
  list-style-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAD8AAAC5CAYAAACftucaAAAAAXNSR0IArs4c6QAAAAZiS0dEAAAAAAAA%2BUO7fwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9oLChIqMDEMzwYAAAtYSURBVHja7Z1dbFzFFcf%2FM%2Ffu3bsfeB2zOAlOHMqHA4LSuIWH0KpK0vIQ1PDQNlJ4iZCCkaJiAYUQRTSI8BAUCSlCCg8IApIlnhJUEBWKhJw8EFESUZpYjfPpj3yQ2MbZrO3d9b17Z%2Bb0Ibs0cXbtDd1dj8P8pHlY7%2FXcOfecuTNzd%2F73AAbDTw5Wh%2FptALxO9hAAVShUKLNmPADghRde%2BA2A39XjXPl8%2FvtMJvPvrq6ubwCI6S4Aq1eIEdGfAXQSXW0LYzU5NU1MTGQ%2B%2FPDDQz09PYd2797dDUCWO9iuW%2F9ibK%2BU8hyAdVLKxZxzMMao2ueJx%2BPhZ555pn3z5s0%2BgANaGA8AlmUdDoLAYYytE0I027ZNNYgwz3VdlzEWmSmyOeqMlPKwUupLAJNCiFp1MSilZuzWdr2Nd103n81m%2F8k5X6yUehQAcV5dH3DOqXhv0crzACCEuCiE6CEiXwhx7fBUlaKUooLn9TM%2BkUiIIAj6pZSnpZQIggCFBl9Xnn%2F%2B%2BQe6u7sbS303XSlcAD2NL3g%2FLaXsV1ehayYlPxQhRGLHjh2%2F3LZt233ZbJaVOqZMge7G54QQQ0opCCFKetCyLB6Px%2BPffvvtPRs3bnzk6NGjsUo8T0SktfFBEPhBEKSUUkoIQUR0Q99ljMG2bUQikbDnefO3bdv26Pvvv7%2B4ENNli%2FbGCyGU7%2FuTVKBU6DPGyLZt2LYNx3GsaDSa%2BOKLLx585ZVXlg0NDTnThH1Ffd6eReMhpVTRaJQKYzNNHZ%2BKnr%2F2T7ZtRxKJRJKIbCKaLFe%2F1sYHQcCUUvY1BqupYzPnnK6dBTqOQ2vXrh1btWrVRSGEN81gTrp73maMJQrhjnKrL8uyAACLFi0KOjo6RufPn38qCIKhGarXPuxt13UXFm9snHNVYjFEjuNg5cqVE08%2B%2BeRFxtgJKWWukhmu1sanUqlwW1vbMqUUHMdRpVZ4%2BXyebdiwYbS9vf20EOJs8UJVgrbGHzx4kCmlWjnndxIR2batGGM3tPbtt9%2F%2BDxH5UsrRm1z%2F6xv2ly5diixbtuz3hUUNhcPhkp5XSl34kQ8%2B9Az77u5ulkgkfuW6bhsAFYlElGVZqprn4JzrOb2NRCL3Njc3ryMicM4RjUZVDU4jC6MgaeP548eP3xuLxf4CwGaMIZFIiFJ3%2Bf%2FnaRmAcDqdviCEyGlj%2FOjo6FNKqT8REbMsi2KxmLIsq9qPsWQmk7mwdevWEc%2FzThbm%2BtNeqZqzevXquj26JqJJ3%2FePHjhwYD80eHRtA7DqFGA%2FLGzwvx8uDAaDwWAwGAwGg8FgMBgMBoPBYDDMAYzSotYYpQXRUgB%2FqLHSAgMDA%2FZnn33mVKK0YPXsY1LKVgB3%2Bb7PLMtCLcQGjLHE2NjYz7Zu3eru2rVrJ4Cg3LH1VlqcC4IgxjlPTk5OMtd1qQY%2FU19paGiwGWMPQzexgZSyD0AjY4xns1kWi8VqsTMj0Flp8R1jrMX3fcYYo3A4TFUOfVWJ0mJWdmMJIS4CaCYiK5PJoAYbkpTWSgspZRqAzOVylM1mSUqpppbOzs6ff%2Fzxx42lvpuuXN3Erff20zSAuO%2F7VjabJdu2b2htOBxu3Lt3b8uhQ4f6X3755eOJRKKiCCmoN%2FT0fMH4nJRSep6nMpmMEkLIqYVzzubNmxcfHR1dumnTpsf2798fK3Xc1KKUkrpvOfcBCM%2FzmOd5aGhokFPHfSml5JyraDQaklIu6Orqeuyrr746%2FtJLL%2FXNdc8rIYScnJyUnudJz%2FNKeVAxxhRjTNm2zZLJZOLcuXO%2FePHFFx%2Fp7e0NlfP8XOjzEEKoXC6nAMD3fTW13yulFOf8umhobGyM3HHHHc2WZdlCCFlmKq192LNMJiMnJyd5YUEiHMeZOjira3do2rZNTzzxxJUVK1acGx0dzXqeV854%2FcUGqVSKip4nIllQV17n%2BeIcoLm5Ob9%2B%2FfrhpqamY4ODg9%2FNsIiS2hs%2FPDxMmUxGWpaFUCgUTBUWE5HinKvly5ePrVmz5vz4%2BHjP%2BfPnsxWOdvoan0qlwsPDwySlVIlEQpbqv57n0dNPP32pvb29t7%2B%2Fv08IUelMUGmttDhy5Eg4nU4TAJo%2Ff35Qyvh33nnnGyGE19vbO3Kz6yetlRZ9fX1cSqksy6IFCxYEU%2Fs7APT29g7%2B2IWNtkqLffv2RcfGxhQALFmyJIhEIkJKWc2FjZ4Co08%2F%2FTQ%2BNDRkAaBIJKLa29v9ahpeGBJD2ikt1q9f7w4MDLiF8RsrVqyYDIVCqlrGx%2BNx3tbW1jg4ONigldKir6%2FvgfHx8YVExGzbppaWlqDaT3GIiAYHB61du3Y97HneURilhVFaGAwGg8FgMBgMBoPBYDAYDAaDwWDQHKO0qDVGaUG0FsDfaqy0kNlsNr179%2B4DuuW02COlPAvgKSJqZ4zVJKdFNBp1nn322V9v2rRJz5wWAFyl1P3FF%2FpWmcBxnGglOS1mQ2lxmDHWwhhbKKVM1EBmAgBc95wWrYyx1cDVPTRV7mLQWmnBOT9q2%2FZvlVLRGvR9%2FXNaBEHwLykllFIgohvK5s2blxw8eDBe6rvpitbGF7yfFkKcLvdifwDk%2B35s%2B%2FbtbTt27FiUy%2BUqzmkxFzIb5IQQQ8WGUgk45zwSiUS%2B%2FvrrOzs7O9t6e3tdqgBA84QexZwWRERSymKjryucc4RCIbiuG8pkMk2vv%2F76%2FV1dXc3lImUuef66nBaljGeMkWVZKOzK5o7jxD7%2F%2FPO7Xn311XtGRkbs6S7AnMhpURySSuW0KEyMaMpnJxaLNRLRBSLyywx1NNdyWpQyHKFQ6IfPjuNg7dq1mZUrV15WSgXT1T8ncloUjS8z1lMxm0lLS4vo6OgYW7BgwQWlVGqG6vWXmcTj8daix0tlNije8FatWpVbs2bNZc75WaWUX0n92istFi9evKqQ1oFKed73fWzYsGGsvb39glJqGDPspb3ZGd6sKS0AtFqWtajwkv%2BST13eeuutAVyVg4%2FdMtPbS5cuRe6%2B%2B%2B6nCsOZCoVCqsx4%2FT0RpVF5tjK9h7ru7m6WTCaXO47zIAByHOcG4WAVVnVMS%2BPj8fh9LS0tnYUbGjmOU4s3J%2BS1U1qcPHnyvmQyuZ2IOGOMotGorLLXGYDQxMTEgFZKi1Qqtd6yrA2FBpLruqoGj7GCbDY7sGXLllMmp4VRWhgMBoPBYDAYDAaDwWAwGAwGg8FgMBj0pW5Ki46OjopfelfJjulpEJzzvwsh%2FvrBBx9cnO7Auv1K%2B95771mvvfaarPV5lFL2%2BPj4H33fB4B1Wni%2ByJtvvlnzC5DL5TAyMiLefffdsBaeL7JlyxZr586dNb0A%2BXwejLEZbZuV3VjX7qqsBZZlVaTempXdWM8995xVUFfVtGjpeaD6upqpdVdS%2F6xtOd%2B4caNVbGS50traypLJJGY6rlTR2vPAzKrKJUuWYN68eWxgYAAnTpyoaGNh0fPaG19JaN52221s6dKluP3229HT00MTExM%2FDeOJCEophEIhLFy4kMXjcZw%2BfRqDg4NUjT6vddgXjS8Si8XYQw89hKamJhw7dozy%2BXzZeue85xljN%2Byb55zDcRxYllX2%2F2%2BJG95Uz0spceTIETp79ixc153bxlfSL4vGp9NpHD58mIQQFIvFpjVuTvT5Sm94p06dojNnziAcDpPrurfG3X6mBl6%2BfBn9%2Ff105coVRKNRqvRtC7dE2J8%2Ffx6cc4rFYjddr9bG79mzZ8ZlbTQapR97UbXt83v37pW1jihtPV%2FLFZ3Wxn%2FyySc19XpxhOCcCyJi072Voa7Gf%2FTRRzKbzdb0HFJKpFIp2dDQ8A8ATQAuz7rxb7zxhjxz5kw9upRIJpP7Hn%2F88d0A8tMOtfUynojW1elUCsA5AGcYY6MwGAwGA%2FBfWUXTyWEAUBwAAAAASUVORK5CYII%3D") !important;
  -moz-image-region: rect(0 60px 32px 20px) !important;
  padding: 0 !important;
  margin-top: 1px !important;
  margin-right: -5px !important;
}
toolbar[iconsize="small"][mode="icons"] #forward-button:not([disabled="true"]):hover:active {
  -moz-image-region: rect(150px 60px 183px 20px) !important;
}
toolbar[iconsize="small"][mode="icons"] #forward-button:not([disabled="true"]):hover {
  -moz-image-region: rect(100px 60px 132px 20px) !important;
}
toolbar[iconsize="small"][mode="icons"] #forward-button[disabled="true"] {
  -moz-image-region: rect(50px 60px 82px 20px) !important;
}

```

Also I recommend this addon [https://addons.mozilla.org/en-US/firefox/addon/tab-utilities/](https://addons.mozilla.org/en-US/firefox/addon/tab-utilities/)

It gives you multi row tabs and when closing tabbs they dont change the size until mouse is moved away from tabbar (like google chrome)

---

### Post by CreativeReach on 2011-05-19
Wow looks great, but just in what file do I put that in?

---

### Post by arzali on 2011-05-19
You can put it into the userChrome.css in your profile folder

/home/<your username>/.mozilla/firefox/(some random digits).default/chrome

Copy and paste the code above into userChrome.css (create if not existent) restart firefox.

Another way is to user the stylish addon. You can find a good howto here [http://www.omgubuntu.co.uk/2011/04/give-firefox-4-a-internet-explorer-9-makeover/](http://www.omgubuntu.co.uk/2011/04/give-firefox-4-a-internet-explorer-9-makeover/)

---

### Post by CreativeReach on 2011-05-19
I used stylish, but what about the buttons? do I have to have the elementary theme?

---

### Post by CreativeReach on 2011-05-19
Also I cant seem to get the refresh button back in the omni bar.

---

### Post by arzali on 2011-05-19
for elementery buttons just use the second code block above

for the reload button the order is important

"urlbar" "reload button" "stop button"

---

### Post by Oxwivi on 2011-05-21
So no need to install the Elementary theme onto Ubuntu itself?

---

### Post by el_koraco on 2011-05-21
Kind sir, if thou does not mind, might ye tell me how ye got the buttons in Nautilus E to look like that? I use the standard eOS theme, and the buttons are green and blue.

---

### Post by arzali on 2011-05-22
> **Oxwivi said:**
> So no need to install the Elementary theme onto Ubuntu itself?

For back forward buttons on firefox? no

---

### Post by j0c1323 on 2011-08-18
Working with Firefox 6 and it look very elegant. Thanx

---

### Post by j0c1323 on 2011-08-18
> **el_koraco said:**
> Kind sir, if thou does not mind, might ye tell me how ye got the buttons in Nautilus E to look like that? I use the standard eOS theme, and the buttons are green and blue.

I want to know that too

---

