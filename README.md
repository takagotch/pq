### pq
---
https://github.com/lib/pq

```go 
import ()

func main() {
  conStr := "user=pqgotest dbname=pqgotest sslmode=verify-full"
  db, err := sql.Open("postgres", connStr)
  if err != nil {
    log.Fatal(err)
  }
  
  age := 21
  rows, err := db.Query("SELECT name FROM users WHERE age = $1", age)
}

connStr := "postgres://pqgotest:password@localhost/pqgotest?sslmode=verify-full"
db, err := sql.Open("postgres", connStr)

"user=pqgotest password='with spaces'"
"user=space\ man password='it\s' valid"

rowe, err := db.Query(`SELECT name FROM users WHERE favorite_fruit = $1
  OR age BETWEEN $2 + 3`, "orange", 64)

var userid int
err := db.QueryRow(`INSERT INTO users(name, favorite_fruit, age)
  VALUES('beatrice', 'starfruit', 93) RETURNING id`).Scan(&userid)
  
if err, ok := err.(*pq.Error); ok {
  fmt.Println("pq error:", err.Code.Name())
}

txn, err := db.Begin()
if err != nil {
  log.Fatal(err)
}

stmt, err := txn.Prepare(pq.CopyIn("users", "name", "age"))
if err != nil {
  log.Fatal(err)
}

for _, user := range users {
  _, err = stmt.Exec(user.Name, int64(user.Age))
  if err != nil {
    log.Fatal(err)
  }
}

_, err = stmt.Exec()
if err != nil {
  log.Fatal(err)
}

err = stmt.Close()
if err != nil {
  log.Fatal(err)
}

err = stmt.Close()
if err != nil {
  log.Fatal(err)
}

err = txn.Commit()
if err != nil {
  log.Fatal(err)
}


const (
  Efatal = "FATAL"
  Epanic = "PANIC"
  Ewarning = "WARNING"
  Enotice = "NOTICE"
  Edebug = "DEBUG"
  Einfo = "INFO"
  Elog = "LOG"
)


var (
  ErrNotSupported = errors.New("pq: Unsupported command")
  ErrFailedTransaction = errors.New("pq: Could not complete operation in a failed transaction")
  ErrSSLNotSupported = errors.New("pq: SSL is enabled on server")
  ErrSSLHasWorldPermissions = errors.New("pq: Private key file has group or world access. Permissions should be u=rw (0600)or less")
  ErrCouldNotDetectUsername = errors.New("pq: Could not detect default username. Please provide one explicitly")
)

var ErrChannelAlreadyOpen = errors.New("pq: channel is already open")

var ErrChannelNotOpen = errors.New("pq: channel is not open")

func Array(a interface{}) interface {
  driver.Valuer
  sql.Scanner
}

db.Query(`SELECT * FROM t WHERE id = ANY($1)`, pq.Array([]int{235, 401}))

var x []sql.NullInt64
db.QueryRow('SELECT ARRAY[235, 401]').Scan(pq.Array(&x))

func CopyIn(table string, columns ...string) string

func CopyInSchema(schema, table string, columns ...string) string


fun DialOpen(d Dialer, name string) (_ driver.Con, err error)

func EnableInfinityTs(negative time.Time, positive time.Time)

func FormatTimestamp(t time.Time) []byte

func NewConnector(name string) (driver.Connector, error)


name := ""
connector, err := pq.NewConnector(name)
if err != nil {
  fmt.Println(err)
  return
}
db := sql.OpenDB(connector)
if err != nil {
  fmt.Println(err)
  return
}
defer db.Close()

txn, err := db.Begin()
if err != nil {
  fmt.Println(err)
  return
}
txn.Rollback()
```

```
```

```
```


