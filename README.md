# A UNIX Tutorial

The repo is just a tutorial for merging analogous .csv file in one resulting `.csv` file.  
This is maybe not the fastest or the smartest way, but it seems to work.  

## Content
- three analogous `.csv` files  
- a `backup` folder  

The `backup` folder is needed to keep a not modified copy of the three `.csv` files.  

## Steps

We use [`head`](https://www.computerhope.com/unix/uhead.htm) command to isolate the header from one of the `.csv` file:  
```
head -n 1 a.csv > header.txt
```

We use [`sed`](https://www.geeksforgeeks.org/sed-command-in-linux-unix-with-examples/) to delete the first row in every `.csv` file:  
```
sed -i '1d' *.csv
```

We then [concatenate](https://www.computerhope.com/unix/ucat.htm), [sort](https://www.geeksforgeeks.org/sort-command-linuxunix-examples/), [remove duplicates](https://www.computerhope.com/unix/uuniq.htm) and save all in `result.csv`:  

```
cat *.csv | sort | uniq > result.csv
```

Finally, we re-append the header to `result.csv`:  
```
cat header.txt result.csv
```
