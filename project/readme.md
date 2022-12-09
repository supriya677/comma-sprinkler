def comma_sprinkler(x):
  split_list = list(x.split(","))
  split_space_elements = []
  last_elements = []
  first_elements = []
  txt = ''
# remove_period(dot) function is used to remove period
  def remove_period(dot):
    dot = dot.replace(".", "")
    return dot
  for i in range(len(split_list)-1):
    split_space_elements = split_list[i].split()
    last_elements.append(split_space_elements[len(split_space_elements)-1])
  for i in range(1,len(split_list)):
    split_space_elements = split_list[i].split()
    first_elements.append(split_space_elements[0])
# applying remove_period(dot) function to remove period
  for i in range(len(first_elements)):
    if '.' in first_elements[i]:
      first_elements[i] = remove_period(first_elements[i])
  for i in range(len(last_elements)):
    add_comma = last_elements[i] + str(',')
    add_period = last_elements[i] + str('.')
    txt = x
    txt = txt.replace(add_period,'1234')
    txt = txt.replace(add_comma,'5678')
    txt = txt.replace(last_elements[i],add_comma)
    txt = txt.replace('1234',add_period)
    txt = txt.replace('5678',add_comma)
# adding commas , periods using strings
  for i in range(len(first_elements)):
    add_comma = str(', ') + first_elements[i]
    add_period = str('. ') + first_elements[i]
    txt = txt.replace(add_period,'1234')
    txt = txt.replace(add_comma,'4678')
    add_space = str(' ') + first_elements[i]
    txt = txt.replace(add_space,add_comma)
    txt = txt.replace('1234',add_period)
    txt = txt.replace('4678',add_comma)
    # checking all the functions again
  split_list1 = list(txt.split(","))
  last_elements1 = []
  first_elements1 = []
  for i in range(len(split_list1)-1):
    split_space_elements = split_list1[i].split()
    last_elements1.append(split_space_elements[len(split_space_elements)-1])
  for i in range(1,len(split_list1)):
    split_space_elements = split_list1[i].split()
    first_elements1.append(split_space_elements[0])
  for i in range(len(first_elements1)):
    if '.' in first_elements1[i]:
      first_elements1[i] = remove_period(first_elements1[i])
# condition to check wheather both are same
  if (len(last_elements) == len(last_elements1)) and (len(first_elements) == len(first_elements1)):
    return txt
  else:
    return comma_sprinkler(txt)#recursive function
x=input("Enter the string :- ")
print(comma_sprinkler(x))
