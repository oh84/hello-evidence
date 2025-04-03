## Hello Evidence

### Orders Table

```my_query_summary
select * from needful_things.my_query
```

<DataTable data={my_query_summary} />

```my_query_summary_top100
select
  order_datetime,
  first_name,
  last_name,
  email
from needful_things.my_query
order by order_datetime desc
limit 100
```

<DataTable data={my_query_summary_top100}>
  <Column id=order_datetime title="Order Date" />
  <Column id=first_name />
  <Column id=email />
</DataTable>

```order_by_month
select
  order_month,
  count(*) as orders
from needful_things.my_query
group by order_month
order by order_month desc
limit 12
```

<BarChart
  data={order_by_month}
  x=order_month
  y=orders
  xFmt="mmm yyyy"
  xAxisTitle="Month"
  yAxisTitle="Orders"
/>

### EV Map

```ev_map
select
  State,
  count(*) as ev_station_count
from ev_stations.us_alt_fuel_stations
where State not in ('CA')
group by State order by ev_station_count desc
```

<USMap
  data={ev_map}
  state=State
  abbreviations=true
  value=ev_station_count
/>
