# django

def check(df):
  for i in set(df.chid):
    if len(df[df["chid"]==i])!=12:
      curr = [j  for j in range(1,13) if j not in df[df['chid']==i]['dt'].tolist() ]
      curr_df = pd.DataFrame({"chid":i,"dt":curr,"value":0})
      df = df.append(curr_df).sort_values(by = ['chid','dt'])
  return df

test = check(df)
